
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
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins pipeline completed successfully.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}",
                to: "your-email@example.com"
            )
        }

        failure {
            emailext(
                subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins pipeline failed.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}",
                to: "your-email@example.com"
            )
        }
    }
}
