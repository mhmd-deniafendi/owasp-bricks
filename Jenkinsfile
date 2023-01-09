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
    environmet {
        REGISTRY_AUTH = credentials("dockerhub")
        REGISTRY_ADDRESS = "https://hub.docker.com/"
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages('Build Image'){
        steps{
            script {
                sh '''
                    docker compose build
                    docker compose up -d 
                ''' 
            }
        }
    }
    stages('Deliver to registry'){
        steps{
            script{
                sh '''
                docker image ls
                docker ps -a
                '''
            }
        }
    }
}
