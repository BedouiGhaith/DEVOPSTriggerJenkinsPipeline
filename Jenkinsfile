pipeline {
    agent any
    triggers {
        // PollSCM trigger to periodically check for new commits
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/BedouiGhaith/DEVOPSTriggerJenkinsPipeline.git']]])
            }
        }
        stage('Send Email') {
            steps {
                emailext(
                    subject: "New Commit in the Repository",
                    body: "A new commit has been pushed to the repository.",
                    to: "bedoui.ghaith@gmail.com"
                )
            }
        }
    }
}
