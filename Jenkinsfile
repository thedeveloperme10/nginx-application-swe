pipeline{
    agent any
    stages{
        stage("Build Docker Image"){
            steps{
                script{
                    sh 'docker build -t vsomasun/nginx-extra-credit-swe-645:${BUILD_TIMESTAMP} .'
                }
            }
        }
        stage("Push Docker Image to DockerHub"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                        sh 'docker login -u vsomasun -p ${dockerhubpwd}'
                        sh 'docker push vsomasun/nginx-extra-credit-swe-645:${BUILD_TIMESTAMP}'
                    }
                }
            }
        }
        stage("Deploy to kubernetes"){
            steps{
                script{
                    sh 'whoami'
                }
            }
        }
    }
}