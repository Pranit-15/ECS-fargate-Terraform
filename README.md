**ECS Fargate Terraform Deployment Pipeline
**
This project establishes a seamless deployment pipeline for a web application using GitHub Actions for building and pushing Docker images to Amazon ECR upon changes pushed to the main branch, coupled with Terraform workflows to orchestrate the infrastructure setup on AWS ECS Fargate including VPC, Load Balancer, Target Group, Security Groups, ECS Cluster, ECS Service, ECS Task Definition, ECR, and IAM Role for ECS.

Prerequisites
GitHub repository for the application code.
Terraform Cloud account for running Terraform code.
IAM user with Admin access for accessing AWS resources via Terraform.
AWS credentials (Access Key ID & Secret Access Key) and Terraform API token stored securely as GitHub repository secrets.
Setup Instructions
Create a workspace in Terraform Cloud account and configure API-driven workflow.

Add AWS credentials as environment variables in Terraform Cloud workspace.

Generate an API token in Terraform Cloud user settings.
(Go to User settings -> Tokens and Create an api token)

Store AWS credentials and Terraform API token securely as GitHub repository secrets.
(Go to your Github repo -> Settings -> Secrets -> Actions. Create a new repo secrets and add IAM user’s Access key id & Secret access key along with the terraform Api token we created earlier.)
These repository secrets will be defined in our workflows which we will create next in aws.yaml & terraform.yaml files. These workflows will use the secrets for authentication while deploying and accessing the aws infrastructure.



Configure GitHub Actions workflows for ECS and Terraform in the repository.
(Go to Actions -> New Workflow and search for ecs. Click on configure and commit this file to your main branch. Similarly, Create a workflow for terraform.)



Edit necessary values in workflow files and other configuration files as per instructions provided below.
Resources Needed
VPC
Load Balancer
Target Group
Security Group
IAM Role for ECS
ECS Cluster
ECS Service
ECS Task Definition
ECR Repo
Usage
Clone the repository: GitHub Repo
Replace/Update the following values in the project files as instructed:
Edit aws.yaml file (ECS workflow) and update values in the env block.

Edit terraform.yaml file (Terraform workflow) and comment out the last action for Terraform destroy. (Line 96)

Update AWS account number in demo_ecs_app.json and ecs.tf files. 



Modify Terraform provider settings in provider.tf by  replacing organisation & workspace name with your terraform cloud account details.

Adjust values in .tf and .json files to customize resource configurations.
Replace index.js file with your application file and update Dockerfile accordingly.
Push changes to the main branch to trigger workflows for deployment.

When we push some changes in any file to the main branch, our workflows will get triggered and start deploying our infra on AWS using Terraform & push our application’s docker image to ECR which will in turn update our ECS services as we have set the task definition to pick the latest image from our ECR.
Hence, we have created a code deployment pipeline using Github actions which is automated to get triggered whenever there’s a code change which is pushed to the main branch and a docker image will be created and pushed to ECR.
Terraform will help to create our ECS cluster on AWS using Github workflow and ECS workflow will update the container image whenever there’s a change in the main branch and update the task definition file as well.











Verification
Access the load balancer DNS to validate changes reflected in the deployed application.



