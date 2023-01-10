pipeline {
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS = credentials("Registry")
        REGISTRY_ADDRESS = "https://hub.docker.com/"
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages {
        // stage('Build Image') { 
        //     steps {
        //         println "Build container image"
        //         sh '''
        //             docker compose build
        //             docker image ls
        //         '''
        //     }
        // }
        stage('Login to Registry') { 
            steps {
                println "Trying to login to registry"
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push and Tag Image') { 
            steps {
                sh '''
                    docker tag nginx:alpine 14022021/owasp-brick-nginx:$BUILD_NUMBER
                    docker tag php:fpm-alpine 14022021/owasp-bricks-php:$BUILD_NUMBER
                    docker image ls
                    docker push 14022021/owasp-brick-nginx:$BUILD_NUMBER
                    14022021/owasp-bricks-php:$BUILD_NUMBER
                '''
                println "Tag and push completed"
            }
        }
    }
}
