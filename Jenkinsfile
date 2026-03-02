pipeline {
    agent any 

    environment {
        DOCKER_IMAGE = 'mebaysan/turkey-earthquake-crisis-app'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage ('checkout'){
            steps {
                checkout scm
                echo "Hello word!"
            }
        }
    }

}