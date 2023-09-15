pipeline {
    agent any

    environment {
        // Declare variables in the environment block
        DOTNET_PATH = "C:\\Program Files\\dotnet\\dotnet.exe"  // Update with the actual path
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your repository
                // For example, if using Git:
              https://github.com/muraliv21/JenkinsWebApplicationDemo.git
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Navigate to the workspace directory
                script {
                    def workspaceDir
                   // if (isUnix()) {
                     //   workspaceDir = sh(script: 'pwd', returnStdout: true).toString().trim()
                   // } else {
                        workspaceDir = bat(script: 'echo %cd%', returnStatus: true).toString().trim()
                        echo workspaceDir
                   // }

                    // Run the .NET Core 6 build command using the full path to 'dotnet'
                   // def dotnetPath = "C:\\Program Files\\dotnet\\dotnet.exe"  // Update with the actual path
                    bat "cd ${workspaceDir}"
                 //   bat "\"${dotnetPath}\" build -c Release"
                     bat "\"${DOTNET_PATH}\" build -c Release"
                }
            }
        }
    }
    
    post {
        success {
            // Archive your build artifacts if needed
            archiveArtifacts artifacts: '**/bin/**', allowEmptyArchive: true
        }
    }
}
