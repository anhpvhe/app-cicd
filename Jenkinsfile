pipeline{
    agent any
    // tools{
    //     maven "maven_3_9_6"
    // }
    //  environment {
    //     DOCKER_REGISTRY = 'docker.io'
    //     DOCKER_USERNAME = 'anhpvhe'
    //     DOCKER_CREDENTIALS_ID = 'dockerhub-id' // ID of Jenkins credential storing Docker Hub password
    // }
    stages{
        // stage('Verify tooling'){
        //     steps{
        //         bat '''
        //         docker info
        //         docker version
        //         docker compose version
        //         curl --version
        //         '''
        //     }
        // }
        stage('Build Docker images'){
            steps{
                script{
                    bat 'docker compose build'
                    // bat 'docker tag full-stack-userdashboard-database anhpvhe/full-stack-userdashboard-database'
                    // bat 'docker tag full-stack-userdashboard-backend anhpvhe/full-stack-userdashboard-backend'
                    // bat 'docker tag full-stack-userdashboard-frontend anhpvhe/full-stack-userdashboard-frontend'
                }
            }
        }
        // stage('Login to Docker Registry') {
        //     steps {
        //             withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
        //                 script {
        //                 // Use Docker Hub credentials to login
        //                 def loginCmd = "docker login --username ${DOCKER_USERNAME} --password-stdin ${DOCKER_REGISTRY}"
        //                 withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
        //                     sh returnStatus: true, script: "echo ${DOCKER_PASSWORD} | ${loginCmd}"
        //             }
        //             }
        //         }
        //     }
        // }
        stage('Push images to hub'){
            steps{
                script{
                        withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                            // bat 'echo %dockerhubpwd% | docker login -u anhpvhe --password-stdin docker.io'
                            bat 'echo %dockerhubpwd%'
                        }
                        // bat 'docker tag full-stack-userdashboard-database anhpvhe/full-stack-userdashboard-database'
                        // bat 'docker tag full-stack-userdashboard-backend anhpvhe/full-stack-userdashboard-backend'
                        // bat 'docker tag full-stack-userdashboard-frontend anhpvhe/full-stack-userdashboard-frontend'
                        // bat 'docker push anhpvhe/full-stack-userdashboard-database'
                        // bat 'docker push anhpvhe/full-stack-userdashboard-backend'
                        // bat 'docker push anhpvhe/full-stack-userdashboard-frontend'
                }
            }
        }
    }
//      post {
//         always {
//             // Clean up Docker containers and volumes after the build
//             script {
//                 bat 'docker-compose down -v'
//             }
//         }
//     }
}