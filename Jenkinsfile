pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building the .NET Core application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
            echo "Get the DriverPath ${ChromeDriverPath}"
          }
        }

        stage('Test Log') {
          environment {
            LocalVariable = 'HelloLocal'
          }
          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is the ChromeDriverPath ${ChromeDriverPath} and localvariable Value ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      when {
        branch 'master'
      }
      parallel {
        stage('Deploy') {
          steps {
            input(message: 'Do you want to Deployment ?', id: 'OK')
            echo 'Deploying the app in IIS server'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts(artifacts: 'LogTestFile.txt', fingerprint: true, onlyIfSuccessful: true)
            archiveArtifacts(artifacts: 'pipeline.log', fingerprint: true)
          }
        }

        stage('Test log') {
          steps {
            writeFile(file: 'LogTestFile.txt', text: 'This is automation file log ${ChromeDriverPath}', encoding: 'UTF-8')
          }
        }

      }
    }

  }
  environment {
    ChromeDriverPath = 'C:\\Driver\\Web\\ChromeDriver.exe'
  }
}