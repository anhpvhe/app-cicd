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
                    bat 'docker compose ps'
                }
            }
        }
        stage('Push images to hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                        bat 'docker login -u anhpvhe -p ${dockerhubpwd}'
                    }
                    bat 'docker push anhpvhe/full-stack-userdashboard-database'
                    bat 'docker push anhpvhe/full-stack-userdashboard-backend'
                    bat 'docker push anhpvhe/full-stack-userdashboard-frontend'
                }
            }
        }
    }
post {
        always {
            // Clean up Docker containers and volumes after the build
            script {
                bat 'docker-compose down -v'
                bat 'docker compose ps'
            }
        }
    }
}