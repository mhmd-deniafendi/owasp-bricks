// Environmet Nginx
// def appName_nginx = owasp-bricks-nginx
// def dockerRegistry = https://hub.docker.com/
// def dockerTag = ${BUILD_ID}

// Docker Host
// def remote = [:]
// remote.name = 'sc-playground-deni'
// remote.host = '159.223.58.65'
// remote.user = 'root'
// remote.password = '1234@Solecode'

pipeline {
    agent any
    environment {
        REGISTRY_AUTH = credentials("dockerhub")
        REGISTRY_ADDRESS = "https://hub.docker.com/"
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages {
        stage('Build container'){
            steps {
                println "Build docker image...."                
                sh '''
                docker compose build
                '''
            }
        }
    }
    stages {
        stage('Running container'){
            steps{
                println "Running container...."
                sh '''
                docker compose up -d
                '''
            }
        }
    }
    stages {
        stage('Envinronment check'){
            steps{
                sh script "docker ps -a"
            }
        }
    }
}