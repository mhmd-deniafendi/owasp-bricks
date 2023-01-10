pipeline {
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS = credentials("Registry")
        REGISTRY_ADDRESS = "https://hub.docker.com/"
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages {
        stage('Build Image') { 
            steps {
                println "Build container image"
                sh '''
                    docker version
                    docker compose version
                    docke-compose -v  
                '''
                ehco 'Build Completed'
            }
        }
        stage('Login to Registry') { 
            steps {
                println "Trying to login to registry"
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo 'login completed'
            }
        }
        stage('Environment check') { 
            steps {
                println 'hello world from Deploy stage'
                sh '''
                    docker image ls
                '''
            }
        }
    }
}
