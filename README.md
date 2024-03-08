

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

1. VPC with public and private subnets in 2 availability zones.

2. An Internet Gateway to allow communication between instances in VPS and the Internet.

3. We are using 2 Availability Zones for high availability and fault tolerance.

4. Resources such as Nat Gateway, Bastion Host and Application Load Balancer use Public Subnets.

5. We will put the webservers and database servers in the Private Subnets to protect them.

6. The Public Route Table is assocated with the public subnets and routes traffic to the internet through the internet gateway.

7. The Main Route Table is associated with the private subnets.


