<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Build a Virtual Private Cloud

**Project Link:** [View Project](https://nextwork.ai/projects/7f907ac7-2473-5c15-a8be-edb36581cdba)

**Author:** Stuart

---

## Introducing Today's Project!

In this project, I will demonstrate how to create and configure my own Virtual Private Cloud (VPC), subnets, and an internet gateway using AWS. The goal of this project is to gain hands-on experience with cloud networking, better understand how AWS networking components work together, and improve my skills in building and managing cloud infrastructure.

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will use the AWS VPC console to create my own Virtual Private Cloud (VPC). A VPC provides an isolated network within AWS where I can launch and manage cloud resources. This will allow me to have more control over my network configuration, including IP addressing, subnets, and routing.

### How VPCs work

VPCs are virtual private clouds that isolate your network to a portion of AWS Cloud to where you can store and control your resources and organize how they communication and integrate with each other outside the public internet.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account ever since my AWS account was created. This is because AWS automatically creates one for you when you make an account so you can use some of their services such as EC2 Instances.

![Virtual Private Clouds (VPCs)](https://nextwork.ai/stuart/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_2facf927)

### Defining IPv4 CIDR blocks

An IPv4 CIDR block defines a range of IP addresses. It specifies how many bits are reserved for identifying the network, while the remaining bits determine how many IP addresses can exist within that network. For example, a /16 reserves 16 bits for the network and leaves 16 bits for host addresses. In AWS, we use this to define the address space of a VPC, which can then be divided into smaller subnets

## Subnets

### What I did in this step

In this step, I will create subnet in my vpc because we need to organize our network.

### Creating and configuring subnets

Subnets are like groups and ranges of ip address for a network. There are already subnets existing in my account, one for every avalibility zone.

### Public vs private subnets

My subnet is not considered public yet because it does not have a route to an internet gateway. For a subnet to be public, it needs a route table with a route that directs internet-bound traffic to an internet gateway attached to the VPC. Without this route, resources in the subnet cannot directly communicate with the internet through the internet gateway.

![Subnets](https://nextwork.ai/stuart/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled auto-assign public IPv4 addresses. This setting makes sure my EC2 instances get a public ip address so that they can communicate with the internet.

## Internet gateways

### What I did in this step

In this step, I will connect my VPC to the internet using an internet gateway because we need our private cloud to be able to communicate with the internet.

### Setting up internet gateways

An internet gateway is an AWS networking component that allows resources within a VPC to communicate with the internet. It acts as a connection between the VPC and the internet, allowing resources in public subnets to send and receive internet traffic when the proper routing and permissions are configured.

Attaching an internet gateway to a VPC means your VPC can now talk to the internet. If I missed this step your VPC would not be able to talk to the internet.

![Internet gateways](https://nextwork.ai/stuart/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_4ae90410)

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will use AWS CloudShell to set up a VPC, subnet and internet gateway because I want to see if it is faster than using the GUI.

### Exploring CloudShell and CLI

AWS CloudShell is a terminal that lets you manage AWS resources directly from your browser. CLI (Command Line Interface) is a tool that allows you to create and manage AWS resources using commands instead of clicking through the AWS console.

### Debugging my setup

To set up a VPC or a subnet, you can use the command aws ec2 create-vpc --cidr-block 10.0.0.0/24 --query Vpc.VpcId --output text and  aws ec2 create-subnet --cidr-block 10.0.0.0/25 --vpc-id vpc-0db2385e2edd64b2f  Make sure to avoid errors by including cidr block.

![Using the AWS CLI](https://nextwork.ai/stuart/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to the AWS Console, using CloudShell can be faster if you know the commands. However, the AWS Console is easier to use because it provides a visual interface. Overall, I prefer using the Console because it's easier to navigate and understand, but I also enjoyed using CloudShell and learning how to create AWS resources through commands.

