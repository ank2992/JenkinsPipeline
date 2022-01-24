pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
            echo "Getting the driver path ${testParam} ..."
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        input(message: 'do you want to continue the deployment', id: 'y')
        echo 'Deploy the application'
      }
    }

  }
  environment {
    testParam = '123'
  }
}