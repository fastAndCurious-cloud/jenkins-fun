pipeline {
 agent any
    stages{
        stage("build"){
            steps{
                script{
                        sh 'docker build -t 975054375040.dkr.ecr.eu-west-1.amazonaws.com/myapp:${GIT_COMMIT} .'
                        sh eval '$(aws ecr get-login --region eu-west-1)'
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