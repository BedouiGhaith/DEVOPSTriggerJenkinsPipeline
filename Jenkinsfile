pipeline {
    agent any
    stages {
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
