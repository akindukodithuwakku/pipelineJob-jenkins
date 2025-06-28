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

    stage('confirm deploy to staging'){
      steps{
        timeout(time: 60, unit: 'SECONDS') {
          input(message: 'Okey to deploy?', ok: 'lets doit!')
        }
      }
    }
  stage(' Deploy to staging') {
    steps {
      echo "deploy to staging"
    }
  }
}
