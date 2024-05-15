pipeline{
    agent any
    // tools{
    //     maven "maven_3_9_6"
    // }
    stages{
        stage('Verify tooling'){
            steps{
                bat '''
                docker info
                docker version
                docker compose version
                curl --version
                '''
            }
        }
        stage('Build Docker images'){
            steps{
                script{
                    bat 'docker compose build'
                }
            }
        }
        stage('Push images to hub'){
            steps{
                script{
                    withDockerRegistry(credentialsId: 'dockerhub-pwd'){
                        bat 'docker push anhpvhe/full-stack-userdashboard-database'
                        bat 'docker push anhpvhe/full-stack-userdashboard-backend'
                        bat 'docker push anhpvhe/full-stack-userdashboard-frontend'
                    }
                }
            }
        }
    }
post {
        always {
            // Clean up Docker containers and volumes after the build
            script {
                bat 'docker-compose down -v'
            }
        }
    }
}