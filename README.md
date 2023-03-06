# DATABASE MIGRATION USING AWS DATABASE MIGRATION SERVICE

For this hands-on project I will be migrating a simple web application (wordpress) from an on-premises environment into AWS. The on-premises environment is a virtual web server (simulated using EC2) and a self-managed MariaDB database server (also simulated via EC2). I will be migrating this simulated on-premise enviroment into AWS and running the architecture on an EC2 webserver and RDS managed SQL database.

**Note: to create the full Architectural diagram on lucidcharts and insert the image and link here**

## STEP 1: CREATING THE SIMULATED ON-PREMISE INFRASTRUCTURE

The first thing I will do is to create the infrastructure that I am going to migrate to AWS later. This is simulated infrastructure of an `on-premise` enviroment that one would traditionally find in a production setting.

I am going to use a one-click deployment to create the base lab infrastructure.This I will do by clicking this link https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/aws-dms-database-migration/DMS.yaml&stackName=DMS

If you following along, you will need to make sure that you are in the `N.Virginia` Region to create this stack.

**To insert images of stack setup and creation**

I will take note of the `parameter` values as I will be using them at a later stage.

**To insert image showing parameter values**

 + DBName
 + DBPassword
 + DBRootPassword
 + DBUser
 
 
 Check the acknowledgement box and click `Create stack`.
 
 **to insert image of acknowledgement and create stack button**
 
 
 The resources will start creating. Wait for the stack to show as `CREATE_COMPLETE`.
 
 ## STEP 1 COMPLETION AND VERIFICATION
 
 Once the stack is in the `CREATE_COMPLETE` status, I will have simulated an `on-premises` environment and an AWS environment.
 
Now I verify that my infrastructure is up and running before I can move to the next step. To do so, I follow the following steps:

In the search bar, I type EC2 and choose EC2 to navigate to the `EC2 console`. 

**to insert image showing EC2 in search bar**

From the `EC2 Dashboard` in the Resources panel Click `Instances (running)`

**to insert an image showing ec2 dashboard**

I notice that there are 2 instances running `CatWeb` and `CatDB` 

**to insert an image showing 2 runing instances**

Select the `CatWeb instance` at the bottom under the `Details` tab copy the `Public IPv4 DNS` of the `CatWeb` instance.

**to insert image of the public dns**

Paste the copied link in a new tab in your browser and press `Enter`.

You should see the `Animals4life Hall of Fame` load... this is running from the simulated `on-premises` environment using the CatDB MariaDB instance

**to insert image of Animal4life**

This verifies that my Infrastructure is running.   



 
 
 
 
 
 
 
 
 
 
 
 
 
 
