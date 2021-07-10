[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A?sub_confirmation=1)


#### What is Infrastructure as Code?
You can create your cloud infrastructure by clicking through the Management Console, the web interface offered by AWS. But automating the process of provisioning and updating your infrastructure allows you to increase reliability and decrease effort. Describing the target state of your infrastructure in code and using a tool to transform the current state of your infrastructure into the target state is called Infrastructure as Code.

AWS is offering an Infrastructure as Code tool: AWS CloudFormation. You can define your infrastructure consisting of virtual machines, networking configuration, databases, and any other AWS service within a template. CloudFormation can use the template containing the target state to create or update your infrastructure.

####  What is a delivery pipeline?
Beside Infrastructure as Code every DevOps toolbox should contain delivery pipelines as well. Pushing every source code change through an automated pipeline ending with a deployment to your production system is called Continuous Delivery. A delivery pipeline defines the process of deploying changes to production. It consists at least of the following steps:

- Building and Packaging
- Testing small units and the whole system
- Deploying to production

Think of a delivery pipeline as the assembly line in a DevOps world. AWS is offering a service allowing you to define and execute delivery pipelines: AWS CodePipeline.

####  Delivery Pipeline as Code
Your delivery pipeline will become as valuable to your company as an assembly line within a factory. It contains all the knowledge needed to deploy a change to production.

Therefore creating the delivery pipeline should be reproducible and automated in the same way as creating your infrastructure. The delivery pipeline itself should be defined in code. Again, Infrastructure as Code is the tool of your choice.

####  Example: CloudFormation and CodePipeline
The following example shows how to use Infrastructure as Code to create a deployment pipeline. The example uses CodePipeline and CloudFormation to deploy a static website on EC2.

- Source: References a GitHub repository. A commit to the repository triggers the deployment pipeline automatically.
- Deploy: CodeDeploy is used to deploy a static web application on EC2.
- Test: A Lambda function sends HTTP request to the EC2 instance to validate the deployment.


# Example of a Continuous Delivery pipeline with AWS CodePipeline and CodeDeploy using CloudFormation

Creating a simple Continuous Delivery pipeline allowing you to push changes from your GitHub repository to your EC2 Instances.

## Services

The following AWS services are used to create a Continuous Delivery pipeline.

* CodePipeline
* CodeDeploy
* CloudFormation
* EC2
* S3
* IAM

## Setup

Fork this repository.

Use the `./setup.sh` script to create a Continuous Delivery pipeline.

Note: The script will create a CloudFormation stack which launches an EC2 instance into the default VPC of your default region. 
(Try using us-east-1a or change it in scripts, also change the bucketname as per your own s3 bucketname.)
The script will ask you for:
* GitHub repository
* GitHub owner (username of individual or organisation)
* GitHub [OAuth Token with access to Repo](https://github.com/settings/tokens).

It might take a few minutes until the CodePipeline job has finished and the EC2 Instance is able to answer your HTTP request.

Looks something like this -

```
prasanjit@Prasanjits-Mac codepipeline-codedeploy-example % ./setup.sh
Enter the Stack name:
awslug
Enter the GitHub repository:
codepipeline-codedeploy-example
Enter the GitHub owner:
prasanjit-
Enter the GitHub OAuth Token:
ghx_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
{
    "StackId": "arn:aws:cloudformation:us-east-1:879566836351:stack/awslug/da9b6d90-e14e-11eb-92cf-0e1cfc6fd327"
}
Creating the CloudFormation stack, this will take a few minutes ...
Done! Send an HTTP request to the following URL, please.

http://ec2-184-72-211-129.compute-1.amazonaws.com
```


