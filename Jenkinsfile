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
                    
                    // Read the content of the README.md file
                    def readmeContent = readFile('README.md')
                    
                    // Send an email with the README.md content
                    emailext subject: "Build Successful - ${currentBuild.fullDisplayName}",
                      body: "The build was successful. Thanks for your contribution!",
                      to: "${currentBuild.committer_email}",
                      recipientProviders: [[$class: 'RequesterRecipientProvider']]
                }
            }
        }
    }
}
