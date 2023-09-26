pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout the Git repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/votre-nom-utilisateur/votre-depot.git']]])
            }
        }
        stage('Send Email') {
            steps {
                // Find the README.md file in the workspace
                def readmeFilePath = findFiles(glob: '**/README.md').first()
                if (readmeFilePath != null) {
                    // Send an email with the README.md file as an attachment
                    emailext(
                        subject: "New Commit with README.md",
                        body: "A new commit was made with changes to the README.md file.",
                        mimeType: 'text/plain',
                        to: 'bedoui.ghaith@gmail.com',
                        attachmentsPattern: "**/README.md"
                    )
                } else {
                    echo "No README.md file found in the workspace."
                }
            }
        }
    }
}
