

pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                println 'hello world from Build stage...'
            }
        }
        stage('Test') { 
            steps {
                sh '''
                    docker compose -v
                '''
            }
        }
        stage('Deploy') { 
            steps {
                println 'hello world from Deploy stage...'
            }
        }
    }
}