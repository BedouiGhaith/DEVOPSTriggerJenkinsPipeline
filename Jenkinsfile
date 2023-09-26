pipeline {
    agent any
    triggers {
        // PollSCM trigger to periodically check for new commits
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from the Git repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/BedouiGhaith/DEVOPSTriggerJenkinsPipeline.git']]])
                    
                    // Send an email after checkout
                    mail(
                        subject: "Test Email",
                        body: "Test",
                        to: "bedoui.ghaith@gmail.com"
                    )
                }
            }
        }
    }
}
