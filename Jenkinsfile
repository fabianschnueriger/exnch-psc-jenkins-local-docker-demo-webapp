node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'DockerHub') {

        def customImage = docker.build("fabianschnueriger/exnch-psc-jenkins-local-docker-demo-webapp")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}