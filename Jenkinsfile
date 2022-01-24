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

        stage('Test Log') {
          environment {
            LocalVariable = 'HelloLocal'
          }
          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is an automation file. Env var is ${testParam} local variable is ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      when {
          branch 'main'
        }
      parallel {
        stage('Deploy') {
          steps {
            input(message: 'do you agree for deployment?', id: 'y')
            echo 'Deploy the application'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'LogTestFile.txt'
          }
        }

      }
    }

  }
  environment {
    testParam = '123'
  }
}
