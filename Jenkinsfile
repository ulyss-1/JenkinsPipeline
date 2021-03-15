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
}