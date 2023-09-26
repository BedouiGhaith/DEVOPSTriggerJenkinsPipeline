pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code repository here
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Add your build steps here
                // For example: sh 'mvn clean package'
            }
        }
    }
    
    post {
        success {
            script {
                def committerEmail = sh(script: 'git log -1 --pretty=format:%ae', returnStdout: true).trim()
                emailext to: "${committerEmail}",
                         subject: "Build Successful",
                         body: "Your commit has been successfully built and tested."
            }
        }
    }
}
