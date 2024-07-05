# AWS networking: Accessing Private Instance via Public Instance

 # Setting Up a Virtual Private Cloud (VPC)

Objective: Create a VPC to isolate resources.

1)  Log into AWS Management Console.
2)	Navigate to the VPC dashboard.
3)	Click on "Create VPC".
4)	Enter details:
5)	Name: my-new-vpc
6)	IPv4 CIDR block: 10.0.0.0/16 (explained as a range of IP addresses available within the VPC).
7)	Click "Create VPC".

# Creating Public and Private Subnets

Objective: Establish separate network segments within the VPC for public and private resources.
Navigate to the Subnets section within the VPC dashboard.

# Public Subnet:
1) Click on "Create Subnet".
2) Name: public-subnet
3) VPC: my-new-vpc
4) Availability Zone: us-east-1a
5) IPv4 CIDR block: 10.0.0.0/24 
 # Private Subnet:
1) Name: private-subnet
2) VPC: my-new-vpc
3) Availability Zone: us-east-1b
4) IPv4 CIDR block: 10.0.1.0/24

# Launching EC2 Instances

# Launching a Public EC2 Instance

Objective: Deploy an Amazon EC2 instance in the public subnet.

1) Navigate to the EC2 dashboard.
2) Click on "Launch Instance".
3) Configure instance details:
4) Name: my-public-instance
5) Instance Type: t2.micro
6) Network: my-new-vpc
7) Subnet: public-subnet
8) Auto-assign Public IP: Enable
9) Security Group: Create or select SG-public with SSH rule.
10) Launch the instance.
11) Availability Zone: us-east-1a



# Launching a Private EC2 Instance

Objective: Deploy another EC2 instance in the private subnet.

1) Navigate to the EC2 dashboard.
2) Click on "Launch Instance".
3) Configure instance details:
4) Name: my-private-instance
5) Instance Type: t2.micro
6) Network: my-new-vpc
7) Subnet: private-subnet
8) Security Group: Create or select SG-private with SSH rule.
9) Launch the instance.
10) Availability Zone: us-east-1b


# Internet Access with Internet Gateway

Setting Up Internet Gateway

Objective: Enable internet access for resources in the public subnet.

1) Navigate to the VPC dashboard.
2) Click on "Internet Gateways".
3) Create a new Internet Gateway named my-internet-gateway.
4) Attach the Internet Gateway to my-new-vpc.

# Configuring Route Tables

Objective: Direct traffic from the public subnet to the Internet Gateway.

1) Navigate to the Route Tables section in the VPC dashboard.
2) Create a new route table for the public subnet named public-route-table.
3) Edit the public-route-table:
4) Add a route:
5) Destination: 0.0.0.0/0
6) Target: my-internet-gateway
7) Associate the public-route-table with the public-subnet.

# Accessing Private Instance via Public Instance
•	Accessing the Private Instance



