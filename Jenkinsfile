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
                        subject: "New Commit in the Repository",
                        body: "A new commit has been pushed to the repository.",
                        to: "bedoui.ghaith@gmail.com",
                        attachmentsPattern: '**/README.txt'
                    )
                }
            }
        }
    }
}
