pipeline {
    agent any

    stages {
        stage('Send Email') {
            steps {
                script {
                    // Obtain the committer's email address from the webhook payload
                    def committerEmail = env.GIT_COMMITTER_EMAIL

                    if (committerEmail) {
                        emailext subject: "Commit Notification",
                                  body: "A commit has been made to the repository.",
                                  to: committerEmail,
                                  recipientProviders: [[$class: 'CulpritsRecipientProvider']]
                    } else {
                        echo "Committer email not found in the webhook payload."
                    }
                }
            }
        }
    }
}
