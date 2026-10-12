
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building web application'
                bat 'dir'
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist style.css exit /b 1'
                bat 'if not exist script.js exit /b 1'
                echo 'Build successful'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application files'
                bat 'findstr /I /C:"<!DOCTYPE html>" index.html'
                bat 'findstr /I /C:"function showMessage" script.js'
                echo 'Tests passed'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website'
                bat 'if not exist deployed-site mkdir deployed-site'
                bat 'copy /Y index.html deployed-site\\index.html'
                bat 'copy /Y style.css deployed-site\\style.css'
                bat 'copy /Y script.js deployed-site\\script.js'
                echo 'Deployment successful'
            }
        }
    }

    post {
        success {
            echo 'CI/CD pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}
