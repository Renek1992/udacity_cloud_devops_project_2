# Udacity-IaC
*Project: Deploy a high-availability web app using CloudFormation*

## Infrastructure diagram

The infrastructure diagram shows the ask architecture with 4 servers split across two private subnets. In order for the servers communicate to the public S3 bucket a NAT gateway in each of the public subnets is used. An Application Load Balancer is used to distribute the the traffic load between then different private subnets. 

![alt text](https://github.com/Renek1992/udacity_cloud_devops_project_2/blob/master/images/submission2-architecture.png "Infrastructure diagram")


## Deployment

To deploy the described infrastructure cd into the src folder and follow the next steps.

### Step 1
Build the network infrastructure:
```bash
aws cloudformation create-stack --stack-name NETWORK-high-availability-app --template-body file://NETWORK-high-availability-app.yml --parameters file://NETWORK-high-availability-app.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2
```

### Step 2
Build the server infrastructure:
```bash
aws cloudformation create-stack --stack-name SERVER-high-availability-app --template-body file://SERVER-high-availability-app.yml --parameters file://SERVER-high-availability-app.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2
```

### Step 3
(Optional) in case of changes
```bash
aws cloudformation update-stack --stack-name ...
```

## Project verification

To validate the successfull deployment, check the output of the server cloudformation stack to find the load balancer DNS name. The following link is provided as reference.

link: [http://SERVE-WebAp-SKXJQQIEP37U-1773294403.us-west-2.elb.amazonaws.com]


