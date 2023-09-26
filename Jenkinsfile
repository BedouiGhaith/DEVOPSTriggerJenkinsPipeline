pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your version control system (e.g., Git)
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Your build steps go here
                // For example: sh 'mvn clean install'
            }
        }
    }

    post {
        success {
            // Send an email on successful build
            emailext subject: "Build Successful - ${currentBuild.fullDisplayName}",
                      body: "The build was successful. Thanks for your contribution!",
                      to: "${currentBuild.committer_email}",
                      recipientProviders: [[$class: 'RequesterRecipientProvider']]
        }
        failure {
            // Send an email on build failure
            emailext subject: "Build Failed - ${currentBuild.fullDisplayName}",
                      body: "The build failed. Please check your changes and try again.",
                      to: "${currentBuild.committer_email}",
                      recipientProviders: [[$class: 'RequesterRecipientProvider']]
        }
    }
}
