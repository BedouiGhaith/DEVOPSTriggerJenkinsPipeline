pipeline {
    agent any
    stages {
        stage('Send Email') {
            steps {
                emailext(
                    subject: "Test Email",
                    body: "This is a test email sent from Jenkins.",
                    to: "recipient@example.com",
                    mimeType: 'text/plain'
                )
            }
        }
    }
}
