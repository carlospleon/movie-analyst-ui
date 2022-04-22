pipeline {
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
                sh 'cd /var/lib/jenkins/workspace/CI'
                sh '''
                docker build -t carlospleon/frontend:v1 .
                docker push carlospleon/frontend:v1
                '''
            }
        }
    }
}
