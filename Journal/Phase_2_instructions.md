# DATABASE MIGRATION USING AWS DATABASE MIGRATION SERVICE

## PHASE 2: Establish Network Connectivity between AWS and the simulated On-Premise Environment.

### PHASE 2A Create a VPC peer between the AWS and on-premise enviroment

In this next phase of this hands-on activity, We will go through steps to establish a network connectivity between my simulated on-premise enviroment and AWS. We will do this by creating a peering connection between the two enviroments. Please note that if this were a real world production enviroment we will be using AWS Direct Connect or Virtual Private Network (VPN). In this case we will use VPC peering connection to simulate that.

First, we will go over to the `VPC Console` by typing VPC in the seach bar and clicking VPC. 

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/VPC%201a.png) 

From the VPC dashboard select `Your VPCs`. There are 2 VPCs which we will be creating the peer connection between `awsVPC` with an `IPv4 CIDR` range of `10.16.0.0/16` and `onpremVPC` with an `IPv4 CIDR` range of `192.168.10.0/24`. We will leave this page open in a tab as we will be referencing to it at a later stage.

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201c.png) 

Now, from the VPC dashboard scroll down and select `Peering Connections` open that in a new tab and click `Create peering connections`

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201d.png) 

Under the peering connection settings in the name box type `A4L-ON-PREMISES-TO-AWS`. In the `VPC ID (Requester)` box choose `onpremVPC` from the drop down list, notice that the `CIDR` range is `192.168.10.0/24`. We now set the accepter part of this peering by scrolling down the page in the `VPC ID (Accepter)` box choose `awsVPC` from the drop down list, notice that the `CIDR` range is `10.16.0.0/16`. Scroll down and click `Create Peering Connection`.

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201e.png)

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201f.png)

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201g.png) 

Notice that a VPC peering has been requested and it is pending acceptance. To accept click on `Actions` and choose `Accept request`.

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201h.png) 

A prompt box will open to accept the peering connection. Click `Accept Request` to create the VPC Peering. 

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201j.png)
![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201k.png)


Once you accept the request you will have established a peering connection between the 2 VPCs which creates a secure channel and a gateway object in both VPCs.

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201l.png)

The next step is to configure routing.This we will do in the next step.


### PHASE 2B Create Routes on the on-premise side.

Inorder for the VPC peer to know how to send traffic to the other side of the peering connection we created, we will need to configure routes. Firstly we will configure the routes on the on-premise side by editing the on-premise `Route table` so that the on-premise simulated enviroment knows how to route traffic to the AWS enviroment.

From the `VPC` dashboard we will select `Route tables` and select `onpremPublicRT`

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201m.png) 

At the bottom select the `Routes` tab and click on `Edit routes`.

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201o.png)

Click on `Add route` at this point we will need the `IPv4 CIDR` of the AWS enviroment. 

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201p.png)


The `IPv4 CIDR` we noted earlier for the AWS enviroment was `10.16.0.0/16`. This you will find from the previously opened tab we noted that we will be using at a later stage. From that previously opened tab notice that the `IPv4 CIDR` for `awsVPC` is `10.16.0.0/16`

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201c.png)

Go ahead and enter that `IPv4 CIDR` in the `Destination` box. In the `Target` box we will need to enter the VPC peer, so in the `Target` box drop down list select `Peering Connection`, it should automatically populate the box with the peering connection we configured earlier which should say `A4L-ON-PREMISES-TO-AWS`. Click on that and then click `Save Changes`. 

![](https://github.com/CloudRiRi15/DATABASE-MIGRATION/blob/main/assets/phase_2_images/vpc%201q.png)

This now means our on-premises enviroment knows how to route traffic to the AWS enviroment. Now we configure routes on the AWS side.


### PHASE 2C Create Routes on the AWS side
















