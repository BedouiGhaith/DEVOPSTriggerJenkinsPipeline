pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://https://github.com/BedouiGhaith/DEVOPSTriggerJenkinsPipeline.git']]])
            }
        }
        stage('Send Email') {
            steps {
                emailext(
                    subject: "Nouveau commit dans le dépôt",
                    body: "${currentBuild.fullDisplayName} a été déclenché par ${currentBuild.buildCauses}",
                    to: "bedoui.ghaith@gmail.com",
                    mimeType: 'text/plain',
                    attachmentsPattern: '**/README.txt'
                )
            }
        }
    }
}
