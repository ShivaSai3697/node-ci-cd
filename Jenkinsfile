pipeline {
    agent any

    parameters {
        string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'Docker Image Tag')
    }

    environment {
        DOCKER_IMAGE = 'yourdockerhubuser/node-ci-app'
    }

    stages {
        stage('Pull & Deploy') {
            steps {
                sh """
                docker pull $DOCKER_IMAGE:${IMAGE_TAG}
                docker stop node-app || true
                docker rm node-app || true
                docker run -d --name node-app -p 3000:3000 $DOCKER_IMAGE:${IMAGE_TAG}
                """
            }
        }
    }
}

