pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your version control system (e.g., Git)
                checkout scm
            }
        }
    }

    post {
            emailext subject: "Build Successful - ${currentBuild.fullDisplayName}",
                      body: "The build was successful. Thanks for your contribution!",
                      to: "${currentBuild.committer_email}",
                      recipientProviders: [[$class: 'RequesterRecipientProvider']]
    }
}
