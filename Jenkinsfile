pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/carlospleon/DockerWorkshop.git'
            }
            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    sh 'echo Success'
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh ''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..  '
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
