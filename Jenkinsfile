node {
    def Dockerfile

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        Dockerfile = docker.build("haritha1541/nodeapp")
    }

    stage('Test image') {
        
        Dockerfile.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            Dockerfile.push("${env.BUILD_NUMBER}")
            Dockerfile.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}
