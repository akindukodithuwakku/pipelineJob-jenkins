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
  }
}
