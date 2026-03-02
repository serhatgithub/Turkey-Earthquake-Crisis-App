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
            }
        }
        stage ('Docker Build and Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                    
                sh '''
                    echo "Docker Hub'a giriş yapılıyor..."
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    
                    echo "Docker imajı derleniyor (Build)..."
                    docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .
                    
                    echo "İmaj Docker Hub'a gönderiliyor (Push)..."
                    docker push ${DOCKER_IMAGE}:${DOCKER_TAG}
                    '''
                }
            }
        }
    }

}