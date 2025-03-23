pipeline {
    agent any

    environment {
        IMAGE_NAME = 'vinayakmishra11/studentproject'
        CONTAINER_NAME = 'studentproject'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/vinayakmishra-11/StudentProject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    bat "docker push %IMAGE_NAME%"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    bat "docker stop %CONTAINER_NAME% || exit 0"
                    bat "docker rm %CONTAINER_NAME% || exit 0"
                    bat "docker run -d -p 8000:8000 --name %CONTAINER_NAME% %IMAGE_NAME%"
                }
            }
        }
    }
}
