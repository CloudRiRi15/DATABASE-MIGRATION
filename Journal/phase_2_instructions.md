# DATABASE MIGRATION USING AWS DATABASE MIGRATION SERVICE

## PHASE 2: Establish Network Connectivity between AWS and the simulated On-Premise Environment.

In this next phase of my hands-on activity, I will go through steps to establish a network connectivity between my simulated on-premise enviroment and AWS. I will do this by creating a peering connection between the two enviroments. Please note that if this were a real world production enviroment I will be using AWS Direct Connect or Virtual Private Network (VPN). In this case I will use VPC peering connection to simulate that.

First, I will go over to the `VPC Console` by typing VPC in the seach bar and clicking VPC. 

**to Insert image a**

From the VPC dashboard select `Your VPCs`. There are 2 VPC which I will be creating the peer connection between `awsVPC` with an `IPv4 CIDR` range of `10.16.0.0/16` and `onpremVPC` with an `IPv4 CIDR` range of `192.168.10.0/24`. I will leave this page open in a tab as I will be referencing to it at a later stage.

**to insert image b**

Now, from the VPC dashboard scroll down and select `Peering Connections` and click ` Create VPC Peering`

**to insert image c**

Under the peering connection settings in the name box type `A4L-ON-PREMISES-TO-AWS`. In the `VPC ID (Requester)` box choose `onpremVPC` notice that the `CIDR` range is `192.168.10.0/24`. I now set the accepter part of this peering by scrolling down the page in the `VPC ID (Accepter)` box choose `awsVPC` notice that the `CIDR` range is `10.16.0.0/16`. Scroll down and click `Create Peering Connection`.

**To insert imanges d-f**

Notice that a VPC peering has been requested and it is pending acceptance. To accept click on `Actions` and choose `Accept request`.

**to insert image g**

A prompt box will open to accept the peering connection. Click `Accept Request` to create the VPC Peering. 

**to insert image h**








