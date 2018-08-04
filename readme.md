# Assesment (Wordpress with RDS DB)


## Required:

  - AWS Account access
  - EC2 key pairs file to login to EC2 resource/instance/server
  - Optional: Access key if want to execute it by CLI

## Used: 
  -Cloudformation

## Execution:

#### Create VPC
  - Login to AWSConsole
  - Click and Open CloudFormation Service -> Create Stack 
  - Create Base Infra(VPC,Subnet,NAT,INet Gateway etc.)(support multi AZ) by using multi-AZ cloudformation tempalate "mazVPC.json"
  - Click Next and fill asked parameters likes StackName and change values if you want to spin VPC as per non-default CIDR Block
  - Click Next and the template will create VPC in given region of AWS account
  
#### Spin up Application(Wordpress) Infra
  - Open CloudFormation Service -> Create Create Stack 
  - and execute steps as above using either wpmaz_automode.json or wpmaz_manualmode.json
  - Required : Key file to login to Ec2
  
##### Automode vs Manual mode 
  - In Auto mode template is reffering to exported values of VPC template and spinning Wordpress environment without needing any user input to place its resources in differnt subnets
  
  - In Manual Mode template I have given flexibility to spinn infra as per user requirement by changing or selecting values as per your need.
  
  

Key Point Achieved:

> Launched App server(EC2 with wordpress in private subnet) ensuring app server's security,  
> Launched RDS DB instance in private subnet ensuring app server's security,  
> Private Subnet instance can access internet via NAT Gateway,  
> Public Subnet attached to Internet gateway,  
> Route table policies done,  
> Launched Load Balancer in Public subnet to take request from internet,  
> Implemented using Auto Scalaring group(fault tollerance),  
> High Availability type implementation


### Spin using CLI

- get AWS libiraries to enable aws cli
- get access key and configure cli/get temp singn on token using IAM role
- command:
aws cloudformation create-stack --stack-name <AWS_STACK> --parameters <PARAMETERS IN KEY VALUE FORM> 
 


