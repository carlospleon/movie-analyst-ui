pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                checkout scm

                docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    customImage = docker.build("carlospleon/frontend:v1")
                    customImage.push()
                }
            }
        }
    }
}