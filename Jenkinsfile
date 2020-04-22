node {
   stage('Preparation') {
       // for display purposes
       echo "Preparing"
   }

   stage('Build') {
       // Build an image for scanning
        checkout scm

        docker.withRegistry('https://registry.hub.docker.com', 'DockerHub') {
            def customImage = docker.build("fabianschnueriger/exnch-psc-jenkins-local-docker-demo-webapp")
            /* Push the container to the custom Registry */
            customImage.push()
        }

   }

  stage('Scan') {
    twistlockScan ca: '', 
        cert: '', 
        compliancePolicy: 'critical', 
        containerized: false, 
        dockerAddress: 'unix:///var/run/docker.sock', 
        gracePeriodDays: 0, 
        ignoreImageBuildTime: false, 
        image: 'fabianschnueriger/exnch-psc-jenkins-local-docker-demo-webapp', 
        key: '', 
        logLevel: 'true', 
        policy: 'critical', 
        requirePackageUpdate: false, 
        timeout: 10
    }

  stage('Publish') {
    twistlockPublish ca: '', 
        cert: '', 
        dockerAddress: 'unix:///var/run/docker.sock', 
        image: 'fabianschnueriger/exnch-psc-jenkins-local-docker-demo-webapp', 
        key: '', 
        logLevel: 'true', 
        timeout: 10
    }
}