pipeline {
    agent any

    stages {

        stage('Check Docker') {
            steps {
                echo 'Checking Docker availability'
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                bat 'docker build -t ara-demo .'
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application'
                bat 'docker stop ara-container || exit 0'
                bat 'docker rm ara-container || exit 0'
                bat 'docker run -d -p 8081:80 --name ara-container ara-demo'
            }
        }
    }
}
