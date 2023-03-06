# DATABASE MIGRATION USING AWS DATABASE MIGRATION SERVICE

For this hands-onproject I will be migrating a simple web application (wordpress) from an on-premises environment into AWS. The on-premises environment is a virtual web server (simulated using EC2) and a self-managed MariaDB database server (also simulated via EC2). I will be migrating this simulated on-premise enviroment into AWS and running the architecture on an EC2 webserver and RDS managed SQL database.

**Note: to create a the full Architectural diagram on lucidcharts and insert the image and link here**

## STEP 1: CREATING THE SIMULATED ON-PREMISE INFRASTRUCTURE

The first thing I will do is to create the infrastructure that I am going to migrate to AWS later. This is simulated infrastructure of an on-premise enviroment that one would traditionally find in a production setting.

I am going to use a one-click deployment to create the base lab infrastructure.This I will do by clicking this link https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/aws-dms-database-migration/DMS.yaml&stackName=DMS

You will need to make sure that you are in the N.Virginia Region to create this stack.

**To insert images of stack setup and creation**
