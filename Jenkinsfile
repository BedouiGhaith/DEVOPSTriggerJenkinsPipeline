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
                    mail(
                        subject: "New Commit in the Repository",
                        body: "A new commit has been pushed to the repository. README.md content:\n\n${readmeContent}",
                        to: "bedoui.ghaith@gmail.com",
                    )
                }
            }
        }
    }
}
