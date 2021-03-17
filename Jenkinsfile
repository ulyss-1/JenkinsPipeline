pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building .NET core app'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the app'
            echo '"Get the DriverPath ${ChromeDriverPath}"'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the app in IIS server'
      }
    }

  }
  environment {
    ChromeDriverPath = 'C:\\driver\\Web\\crhomedriver.exe'
  }
}