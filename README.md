

![images](images/Screenshot_1.png)

1. Docker to build the container

2. Git to track changes

3. GitHub to manage the Dockerfile and application code in Git repositories

4. AWS CLI to interact with AWS services from the commandline

5. Flyway to migrate SQL data into RDS database.

6. VS Code to write and edit scripts.

7. Amazon ECR to store the Docker images.

8. Amazon ECS to containerize the web application to AWS cloud.

9. 3 tier VPC with public and private subnets in 2 availability zones.

10. Internet Gateway to allow communication between resources in VPC and the Internet.

11. Nat Gateways to allow resources in the private subnets access to the internet.

12. Amazon MySQL RDS for relationa database.

13. ECS Fargate to run the containerized application.

14. Application Load Balancer to distribute web traffic to the ECS Fargate tasks.

15. Auto Scaling Group to dynamically create new ECS tasks.

16. Route 53 to regiter domain name and create a record set.

17. AWS S3 to store files containing environment variables for the container.

18. IAM Role to grant permission for ECS to execute tasks.

19. Using a Bastion Host to set up an SSH tunnel.

20. Security Group to control inbound and outbound traffic to resources.

21. Certificate Manager to encrypt data in transit.


## Building a Three-Tier AWS Network VPC from Scratch

The 3-tier architecture pattern is a common infrastructure pattern that divides the infrastructure into three layers: one public and two private layers. The public layer acts as a shield to the private layers. The public layer is publicly accessible, while the private layers are only accessible from within the network.
In addition to dividing the network into 3 separate layers we also want to implement some kind of high availability. AWS allows you to achieve high availability by distributing your application across multiple Availability Zones. Each Availability Zone is a physical data center in a different geographic location.

![images](images/Screenshot_2.png)

Here are the components of the above architecture.

1. **VPC** with public and private subnets in 2 availability zones.



2. An **Internet Gateway** to allow communication between instances in VPS and the Internet.

3. We are using 2 **Availability Zones** for high availability and fault tolerance.

4. Resources such as **Nat Gateway, Bastion Host and Application Load Balancer** use Public Subnets.

5. We will put the webservers and database servers in the Private Subnets to protect them.

6. The **Public Route Table** is assocated with the public subnets and routes traffic to the internet through the internet gateway.

7. The **Main Route Table** is associated with the private subnets.


### Step 1: Create a VPC

![images](images/Screenshot_3.png)

Enable DNS Hostname on the VPC

![images](images/Screenshot_4.png)

![images](images/Screenshot_5.png)

Create Internet Gateway

![images](images/Screenshot_6.png)

![images](images/Screenshot_7.png)

Attach the Internet gateway to the VPC that you created to allow the VPC to communicate with the internet.

![images](images/Screenshot_8.png)

![images](images/Screenshot_9.png)

![images](images/Screenshot_10.png)

![images](images/Screenshot_11.png)

Create Public subnets

![images](images/Screenshot_12.png)

Filter by your VPC `Dev VPC` you should see that there are no subnets in this newly created VPC

![images](images/Screenshot_13.png)

Give the subnet a name according to the reference architecture `public subnet az 1`

According to the architecture, the subnet should be in `us-east-1a` so under Availability Zone select that.

Enter the CIDR block that is given in the architecture `10.0.0.0/24`

![images](images/Screenshot_14.png)

![images](images/Screenshot_15.png)

Remember we need 2 subents, one in `us-east-1a` and another in `us-east-1b` Now create the second subnet.

![images](images/Screenshot_16.png)

![images](images/Screenshot_17.png)

Now that we have that we have to enable the auto-assign for the 2 public subnets, this means that everytime you launch an ec2 instance in your subnets, those ec2 instances will be assigned a public ip address. Do this for both subnets.

![images](images/Screenshot_18.png)

![images](images/Screenshot_19.png)

Next thing we do is create a Route Table

![images](images/Screenshot_20.png)

You will find a default Route Table, this route table is a default route table created when you create a VPC. This is the Main route tabe and is private by default.

![images](images/Screenshot_21.png)

On the drop-down select your VPC `Dev VPC`

![images](images/Screenshot_22.png)

![images](images/Screenshot_23.png)

Now that we have a Route Table, the next thing to do is to add a public route to our Route Table. The Public Route will allow the Route Table to route traffic to the Internet

Make sure that you are on the Route Tab and click on `Edit routes`

![images](images/Screenshot_24.png)

![images](images/Screenshot_25.png)

The next thing we are going to do is to associate the two subnets that we created with the public route table.

![images](images/Screenshot_26.png)

![images](images/Screenshot_27.png)

To finish we need to create our 4 Private Subnets.

![images](images/Screenshot_28.png)

![images](images/Screenshot_29.png)

![images](images/Screenshot_30.png)

![images](images/Screenshot_31.png)


