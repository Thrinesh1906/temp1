pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('CHECKOUT') {
            steps {
                git 'https://github.com/Thrinesh1906/temp.git'
            }
        }

        stage('Build') {
            steps {
                dir('demo') {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                dir('demo') {
                    bat 'mvn test'
                }
            }
        }
    }

    post {
        success {
            slackSend message: "✅ Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            mail to: 'your-email@gmail.com',
                 subject: "Build SUCCESS",
                 body: "Build completed successfully"
        }
        failure {
            slackSend message: "❌ Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            mail to: 'your-email@gmail.com',
                 subject: "Build FAILED",
                 body: "Build failed"
        }
    }
}