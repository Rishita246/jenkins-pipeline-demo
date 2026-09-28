pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build completed successfully.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}",
                to: "your-email@example.com"
            )
        }

        failure {
            emailext(
                subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build failed.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}",
                to: "chalumuririshita.23.cse@anits.edu.in"
            )
        }
    }
}
