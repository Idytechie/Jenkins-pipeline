pipeline {
   agent any

   environment {
    AWS_REGION = 'us-east-1'
    IMAGE_ECR_RE7PO = '796973504296.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci'
    ECR_REPO = '79693504296.dkr.ecr.us-east-1.amazonaws.com'
    BRANCH_NAME = 'main'
    GIT_CRED = 'Github-creds'
    GIT_PROJECT_URL = 'https://github.com/Idytechie/Pet-clinic-java.git'

   }

            }
    
        stage('dockerLogin'){
            steps{
                sh 'aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS \
                --password-stdin 796973504296.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
stage('dockerImageBuild'){
        steps{
            sh 'docker build -t jenkins-ci .'
            sh 'docker build -t imageversion .'
        }
}
    stage('dockerImageTag'){
        steps{
            sh "docker tag jenkins-ci:latest\
             $IMAGE_ECR_REPO:latest"
            sh "docker tag imageversion \
            $IMAGE_ECR_REPO:v1.$BUILD_NUMBER"
            }
    }
         
    stage('pushImage'){
        steps{
            sh "docker push \
            $IMAGE_ECR_REPO:latest"
            sh "docker push \
            $IMAGE_ECR_REPO:v1.$BUILD_NUMBER"
        }
    }
    */
    