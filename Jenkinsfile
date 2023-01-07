pipeline {
    agent any
    stages {
        stage('Clone The Repository') {
            steps {
                git 'https://github.com/rajshamz/simple-quiz-app.git'
            }
        }
        stage('Build Docker Container') {
            steps {
                script {
                    def app = docker.build("quiz-app:latest", ".")
                }
            }
        }
        stage('Deploy to Docker Desktop') {
            steps {
                script {
                    sh 'docker stop quiz-app || true'
                    sh 'docker rm quiz-app || true'
                    sh 'docker run --name quiz-app -d -p 8099:8080 quiz-app:latest'
                }
            }
        }
     }
}

