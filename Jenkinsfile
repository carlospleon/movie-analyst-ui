pipeline {
    
    environment {
        registry = "carlospleon/frontend"
        registryCredential = 'dockerhub'
    }

    agent any

    stages {
        stage('Pull') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/carlospleon/movie-analyst-ui.git'
            }
            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    echo 'Success in'
                    pwd()
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('push') {
            steps{
                script {
                   docker.withRegistry( '', registryCredential)  {
                       dockerImage.push()
                   }
                }
            }
        }
    }
}
