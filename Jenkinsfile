pipeline {
    agent any
    stages {
        stage('Send Email') {
            steps {
                emailext(
                    subject: "Test Email",
                    body: "This is a test email sent from Jenkins.",
                    to: "bedoui.ghaith@gmail.com"
                )
            }
        }
    }
}
