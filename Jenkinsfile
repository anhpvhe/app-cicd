pipeline{
    agent any
    stages{
        stage('verify tooling'){
            steps{
                bat '''
                docker info
                docker version
                docker compose version
                curl --version
                '''
            }
        }
        stage('Prune Docker Data'){
            steps{
                bat 'docker system prune -a --volumes -f'
            }
        }
        stage('Start Container'){
            steps{
                bat 'docker compose up -d --no-color --wait'
                bat 'docker compose ps'
            }
        }
    }
    post{
        always{
            bat 'docker compose down --remove-orphans -v'
            bat 'docker compose ps'
        }
    }
}