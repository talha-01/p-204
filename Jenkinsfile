pipeline{
    agent{
        label "master"
    }
    environment{
        ECR_REGISTRY ="282594292356.dkr.ecr.us-east-1.amazonaws.com"
        APP_REPO_NAME = "phonebook-app"
        AWS_REGION = "us-east-1"
    }
    stages{
        stage("Create ECR Repo"){
            steps{
                echo "Creating ECR Repository"
                sh """
                aws ecr create-repository \
                  --repository-name $APP_REPO_NAME \
                  --image-scanning-configuration scanOnPush=false \
                  --image-tag-mutability MUTABLE \
                  --region $AWS_REGION                
                """
            }
        }
        stage("Build App Docker Image"){
            steps{
                echo "Building App Docker image"
            }
        }
        stage("Push Docker Image to ECR Repo"){
            steps{
                echo "Pushing Images to ECR Repo"
            }
        }
        stage("Create Infrastructure for the App"){
            steps{
                echo "Creating Docker Swarm cluster"
            }
        }
        stage("Test the Infrastructure"){
            steps{
                echo "Testing if Docker Swarm is ready"
            }
        }
        stage("Deploy the App on Docker Swarm"){
            steps{
                echo "Deploying the app"
            }
        }
        stage("Test the app"){
            steps{
                echo "Testing the application"
            }
        }                         
    }
    post{
        always{
            echo "Deleting all local images"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "Deleting the ECR Repo due to failure"

            echo "Deleting the Cloud Formation stack due to failure"
        }
    }
}