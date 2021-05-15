pipeline {
 agent any
    stages{
        stage("build"){
            steps{
                script{
                        git 'https://github.com/wardviaene/docker-demo'
                        sh 'docker build -t 975054375040.dkr.ecr.eu-west-1.amazonaws.com/myapp:${GIT_COMMIT} .'
                        echo "build Image completed"
                        sh 'aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 975054375040.dkr.ecr.eu-west-1.amazonaws.com'

                        echo "connected to AWS"
                        sh 'docker push 975054375040.dkr.ecr.eu-west-1.amazonaws.com/myapp:${GIT_COMMIT}'
                }

            }
        }
        stage("test"){
            steps{
                echo "test"
            }
        }
        stage("deploy"){
            steps{
                echo "deploy"
            }
        }
    }
}