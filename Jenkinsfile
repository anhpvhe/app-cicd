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
    }
}