[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A?sub_confirmation=1)

# Example of a Continuous Delivery pipeline with AWS CodePipeline and CodeDeploy

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
