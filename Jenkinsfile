node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        customImage = docker.build("carlospleon/frontend:v1")
        customImage.push()
    }
}