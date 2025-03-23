pipeline {
    agent any
    stages {
        stage("verifying tooling") {
            steps {
                sh '''
                    sudo docker version 
                    sudo docker info
                    sudo docker compose version
                    curl --version
                    jq --version
                '''
            }
        }
        stage("Prune Docker Data") {
            steps {
                sh 'sudo docker system prune -a --volumes -f'
            }
        }
        stage("Start Container") {
            steps{
                sh 'sudo docker compose up -d --no-color --wait'
                sh 'sudo docker compose ps'
            }
        }
    }
}
