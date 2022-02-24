---
published: true
---
## How to Launch a Dockerized Container Using ECS with CDK in Typescript
Launching a PostgreSQL database using PGadmin within a dockerized container seemed like a daunting task, and it took a while for me to figure out. My task had the added complication of automation within AWS ECS for ease of deployment, managability, and scale. Following is a step-by-step breakdown of how to do it, using AWS CDK, in typescript.

The required installation packages are:
AWS CLI
AWS CDK
Typescript
Node.js
NPM

## Initializa a typescript project with CDK
First, Create an empty file folder and name your project. In this case, we will call it "ec2-in-cdk".
Navigate to that folder and then initialize a project:

cdk init app --language = typescript

To allow for autocompiling:

npm run watch

## Import classes
Go to your code editor and view the skeleton project created in the directory you just created. We are going to alter this code for our needs.
We need to adjust the settings so that our AWS user account is in the environment variables. Go to the .bin folder and open the typescript file with the same name as the project. Uncomment the line to specialize the stack for the AWS account and region that are implied by the current CLI configuration.

##(cant remember if I needed to set up a constructor/stack props in the beginning)

## Construct a VPC


## Create Security Groups

## Enable Secrets for PGadmin Credentials

## Define ECS Cluster

## Define Task Definition

## Define Service

## Create an RDS Instance

## Connect RDS to Service

## Finished!
