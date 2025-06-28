pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo "build step"
      }
    }
    stage('Test') {
      parallel {
        stage('Test On Windows') {
          steps {
            echo "Running tests on Windows"
          }
        }
        stage('Test On Linux') {
          steps {
            echo "Running tests on Linux"
          }
        }
      }
    }
    stage('Confirm Deploy to Staging') {
      steps {
        timeout(time: 60, unit: 'SECONDS') {
          input message: 'Okay to deploy?', ok: 'Let\'s do it!'
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        echo "deploy to staging"
      }
    }
    stage('Confirm Deploy to production') {
     steps {
       timeout(time: 60, unit: 'SECONDS') {
         input(message: 'Okay to Deploy?', ok: 'Let\'s Do it!')
       }
     }
   }
    stage('Deploy to Production') {
     steps {
       echo "Deploying to production..."
     }
   }
  }
  post {
    success {
      echo "build success"
    }
    failure {
      echo "build failed"
    }
  }
}
