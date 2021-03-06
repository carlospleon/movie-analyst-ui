pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Pull') {
        steps {
            // Get some code from a GitHub repository
            git branch: 'main', url: 'https://github.com/carlospleon/movie-analyst-ui.git'
        }
        post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.   A
            success {
               sh 'echo Success'
            }
        }
    }
    stage('Build') {
      steps {
        sh 'docker build -t carlospleon/frontend:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push carlospleon/frontend:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
