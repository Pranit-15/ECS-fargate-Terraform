# ecs-fargate-terraform

Assignment:

1. Build a code deployment pipeline for our demo application.
2. By using github action and terraform on AWS ECS Fargate.
3. Creating a stack of github, AWS ECR, ECS and Terraform cloud.   

Github workflow:
1. Deploy to ECS.
2. Terraform.

### List of files created AWS resources through Terraform

1. VPC:
   1. Public Subnets
   2. Private Subnets
   3. Internet Gateway
   4. NAT Gateway
   5. Route Tables
2. Security Groups
3. IAM Role
4. Application Load Balancer
5. Elastic Container Registry
6. ECS Cluster
   1. ECS Service
   2. ECS tasks