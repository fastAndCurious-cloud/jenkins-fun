pipeline {
 agent any
    stages{
        stage("Checkout"){
            steps{
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/wardviaene/docker-demo']]])

            }
        }
        stage("build docker image"){
            steps{
                script{
                    sh 'docker build -t 975054375040.dkr.ecr.eu-west-1.amazonaws.com/myapp:1 .'
                        echo "build Image completed"
                }

            }
        }
        stage("test"){
            steps{
                echo "test"
            }
        }
        stage("upload Image"){
            steps{
                script{

                        sh 'aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 975054375040.dkr.ecr.eu-west-1.amazonaws.com'
                        echo "get-login to ECR successful"
                        sh 'docker push 975054375040.dkr.ecr.eu-west-1.amazonaws.com/myapp:1'
                        echo "pushed image to ECR"
                }

            }
        }
        stage("deploy"){
            steps{
                echo "deploy"
            }
        }
    }
}