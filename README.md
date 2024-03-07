# Docker-ECR-ECS-dynamic-website
Host a Dynamic Web App on AWS with Docker, Amazon ECR, and Amazon ECS

![images](images/Screenshot_1.png)

1. Docker to build the container

2. Git to trach changes

3. GitHub to manage the Dockerfile and application code in Git repositories

4. AWS CLI to interact with AWS services from the commandline

5. Flyway to migrate SQL sata into RDS database.

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

1. Certificate Manager to encrypt data in transit.


