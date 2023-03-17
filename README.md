# Scenario-1

Clone the Repository on your system.

git clone <repository.url>

Step 1: 

1) First deploy the infra.yaml to setup the vpc, subnets etc.

CMD: aws cloudformation create-stack --stack-name ecs-infra-creation --template-body file://Infrastructure.yaml --region 'REGION-NAME' --capabilities CAPABILITY_IAM

Step 2: 

2) Deploy the ECS Cluster with ec2 capabilities and Autoscaling groups.

CMD: aws cloudformation create-stack --stack-name test-ecs-takeaway --template-body file://ECS-cluster.yaml --region 'REGION-NAME' --capabilities CAPABILITY_IAM

Note: In ECS-cluster.yaml file you need to update the values of default with vpcID, SubnetID with the above stack resource values.


Pre-requisite for Service Creation:

Before creating a service you need to create a task definition with the help of jenkins-taskDefinition.json file.

Step 3: 

3) Create a Service in cluster. This will launch a task with jenkins task definition.

CMD: aws cloudformation create-stack --stack-name test-ecs-takeaway --template-body file://ECS-Service-takeaway.yaml --region 'REGION-NAME' --capabilities CAPABILITY_IAM


Note: In ECS-cluster.yaml file you need to update the values of default with vpcID, GroupSubnetID, SubnetID with the above stack resource values.
