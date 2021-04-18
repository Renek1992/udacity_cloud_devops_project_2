# Udacity-IaC
*Project: Deploy a high-availability web app using CloudFormation*

## Infrastructure diagram

![alt text](https://github.com/Renek1992/udacity_cloud_devops_project_2/blob/master/images/submission2-architecture.png "Infrastructure diagram")




## Step 1
Run servers.yml
`aws cloudformation create-stack --stack-name network --template-body file://network.yml --parameters file://network-params.json --capabilities CAPABILITY_IAM`

## Step 2
Run bastion-server.yml
`aws cloudformation create-stack --stack-name bastion-host-server --template-body file://bastion-server.yml --parameters file://bastion-server-params.json --capabilities CAPABILITY_IAM`

## Step 3
Run application-servers.yml
`aws cloudformation create-stack --stack-name application-servers --template-body file://application-servers.yml --parameters file://application-servers-params.json --capabilities CAPABILITY_IAM`