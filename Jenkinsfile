// Environmet Nginx
// def appName_nginx = owasp-bricks-nginx
// def dockerRegistry = https://hub.docker.com/
// def dockerTag = ${BUILD_ID}



pipeline {
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS = credentials("dockerhub")
        REGISTRY_ADDRESS = "https://hub.docker.com/"
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages {
        stage('Build Image') { 
            steps {
                println "Build container image"
                sh '''
                    docker version
                    docker compose -v
                    docker compose build   
                '''
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