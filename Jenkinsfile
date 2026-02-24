pipeline {
    agent { label 'manik' }

    environment {
        DOCKERHUB_USERNAME = "malik0505"
        BACKEND_IMAGE      = "${DOCKERHUB_USERNAME}/mean-backend"
        FRONTEND_IMAGE     = "${DOCKERHUB_USERNAME}/mean-frontend"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/myapp32/mean-crud-devops.git'
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                sh "docker build -t ${BACKEND_IMAGE} ./backend"
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                sh "docker build -t ${FRONTEND_IMAGE} ./frontend"
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-creds',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    sh "echo ${DOCKER_PASS} | docker login -u ${DOCKER_USER} --password-stdin"
                }
            }
        }

        stage('Push Images to DockerHub') {
            steps {
                sh """
                    docker push ${BACKEND_IMAGE}
                    docker push ${FRONTEND_IMAGE}
                """
            }
        }

        stage('Deploy') {
            steps {
                sh """
                    cd mean-crud-devops
                    docker-compose up -d
                """
            }
        }
    }

    post {
        success {
            echo "Deployment Successful!"
        }

        failure {
            echo "Pipeline Failed!"
        }
    }
}