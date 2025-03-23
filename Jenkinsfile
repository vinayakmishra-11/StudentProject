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
                script {
                    withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://index.docker.io/v1/']) {
                        bat "docker login -u vinayakmishra11 -p %DOCKER_PASSWORD%"
                        bat "docker push %IMAGE_NAME%"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Ensure old container is stopped & removed safely
                    bat "docker stop ${CONTAINER_NAME} || echo 'No existing container to stop'"
                    bat "docker rm ${CONTAINER_NAME} || echo 'No existing container to remove'"

                    // Run the new container
                    bat "docker run -d -p 8000:8000 --name ${CONTAINER_NAME} ${IMAGE_NAME}"
                }
            }
        }
    }
}
