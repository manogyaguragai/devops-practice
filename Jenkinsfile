pipeline {
    agent any
    environment {
        DOCKER_COMPOSE_CMD = "docker compose" // Ensure correct compose command
    }
    stages {
        stage("Verifying Tooling") {
            steps {
                sh '''
                    docker --version 
                    docker info
                    docker compose version
                    curl --version
                    jq --version
                '''
            }
        }
        stage("Prune Docker Data") {
            steps {
                sh 'docker system prune -a --volumes -f'
            }
        }
        stage("Start Container") {
            steps {
                sh '${DOCKER_COMPOSE_CMD} up -d --no-color'
                sh '${DOCKER_COMPOSE_CMD} ps'
            }
        }
    }
}
