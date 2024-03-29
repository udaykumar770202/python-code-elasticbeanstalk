# Deploying a Python Application to AWS Elastic Beanstalk using AWS SAM and CloudFormation

![GitHub](https://img.shields.io/badge/license-MIT-blue.svg)

This repository contains an AWS CloudFormation template for deploying a Python application to AWS Elastic Beanstalk. The template automates the creation of resources such as EC2 instances, Elastic Load Balancer, Auto Scaling Group, IAM roles, and CloudWatch logs.

## Prerequisites

Before you begin, ensure you have the following:

- An AWS account with permissions to create resources like Elastic Beanstalk, EC2, IAM roles, etc.
- AWS CLI and AWS SAM CLI installed on your local machine.
- A Python application bundled into a ZIP file.
- Knowledge of your VPC ID, EC2 subnet ID, application environment, instance type, load balancer subnet ID, load balancer visibility, solution stack, S3 bucket name, and ZIP file name for your application code.

## Steps

1. **Install AWS CLI and AWS SAM CLI:**
   - Follow the official AWS CLI installation guide: [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
   - Install AWS SAM CLI using pip:
     ```
     pip install aws-sam-cli
     ```
   - Verify the installations:
     ```
     aws --version
     sam --version
     ```

2. **Prepare Your Application ZIP:**
   - Bundle your Python application into a ZIP file. Ensure it includes all necessary files and dependencies.

3. **Configure AWS Credentials:**
   - Run the AWS CLI configure command to set up your AWS credentials:
     ```
     aws configure
     ```

4. **Deploy Using AWS SAM and CloudFormation:**
   - Upload your CloudFormation template and the application ZIP file to an S3 bucket.
   - Use AWS SAM to deploy the CloudFormation stack and pass environment variables:
   - do sam build in project location, it will build the template
     ```
     sam build
     ```
   - do sam deploy in project location
     ```
     sam deploy --guided
     ```
   - if your facing any issue with CAPABILITY_IAM then run below command
   
     ```     
     sam deploy --template-file template.yaml --stack-name YourStackName --capabilities CAPABILITY_IAM
     ```
     Replace the placeholders with your actual values for VPC ID, subnet ID, environment, instance type, load balancer subnet ID, load balancer visibility, solution stack, S3 bucket name, and ZIP file name. Also, create an `env.json` file containing your environment variables.

## code should be in s3 and while deploying template then need to give bukcet name and key

example

     ```
     BucketName: yourbucketname
     BucketFileName: your zip object
     ```


5. **Access Your Application:**
   - Once deployment is complete, access your Python application using the URL provided by Elastic Beanstalk.

## Additional Notes

- Customize the CloudFormation template as needed for your specific application requirements.
- Adjust scaling policies, instance types, and other settings in the CloudFormation parameters.
- Monitor your application's performance using CloudWatch metrics and logs.

## Troubleshooting

If you encounter any issues during deployment or with your application, refer to AWS documentation or seek assistance from AWS support.

## Contributing

Contributions to this CloudFormation template are welcome. Feel free to submit pull requests or report issues.

## License

This CloudFormation template is licensed under the MIT License.

## try without sam also
you can directly deploy template.yaml in cloudfromation 