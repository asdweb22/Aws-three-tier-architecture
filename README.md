AWS Three-Tier Architecture Design and Deployment Project

**Step 1:**  download github project in your local machine using below link
 - git clone https://github.com/aws-samples/aws-three-tier-web-architecture-workshop.git

**Step 2:**  create s3 bucket on in aws account (asd-3-tier-bucket)

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/9d7a02c0-3e74-4354-bccc-9f2a2aeffcf0)

**Step 3:**  Create ec2-three-tier-access-role and choose aws service ec2 and attach these 2 policies 
 - AmazonSSMManagedInstanceCore
 - AmazonS3ReadOnlyAccess

   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/4058f198-f9ae-4ecd-859e-7ac7c328caa9)
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/0a028323-ff61-469f-a272-02e5841d1357)
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/1a8e8bd7-46b9-4938-b936-b29109835815)
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/2b840953-2583-41ef-9208-18b21a71dbab)


**Step 4:**  Networking and Security
  -VPC
  -Subnets
  -Route Tables  
  -Internet Gateway
  -NAT gateway
  -Security Groups
  
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/c49f537e-73b7-4587-8ebe-5a077b8c246d)
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/14d63e69-fa9c-4828-b93c-0424e63d709a)
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/7ca1fb7e-2f92-42f4-b1f5-6a1ebe96d1d1)
  
  Attach igw to vpc
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/6a5df2f5-5ca3-41cb-9fa9-16cb1f87b4f3)


  Nat gateway created for AZ 1-a
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/636032c9-fa24-4e29-b3b7-b6765ad0107d)

  Nat gateway created for AZ 1-b
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/ef03b97d-fc39-4f40-acb8-b3eb15934ff3)

  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/e43a250f-c3f5-4f1d-abbb-0fd61270ee9c)

**Routing Configuration**
after creating vpc default route table created rename this route table as (Public-Subnet-Route-Table)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/31793e1d-845e-42c0-a290-d4ccb1690f63)

Add Route for IGW
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/93c22aea-c884-4730-919b-030cd889bedb)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/dd85b665-81ee-46a6-a04e-496bf8d4bcac)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/b7dd23b0-37f3-400b-98c2-b1c8b55fb1a0)

**Associate public subnet 1-a and 1b**
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/db5f1d56-39d1-43e4-8664-70f631bd6c47)


**Create private Route table for Az-1a:**

Associate Private subnet Az-1a
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/4ec4fc44-22f4-4618-a45f-19ac9dc7d86b)


Adding route of nat gateway of az-1a in private route table az-1a
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/0563247c-0825-47a6-9d94-f77748d440bc)


**Create private Route table for Az-1b:**
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/45ae251c-bfff-419d-a94b-be921a16d7a7)

Add route nat gatweay of Az- 1b
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/cd8c3f61-f4ec-43b9-8016-5efb12eb2a29)

Associate private subnet Az-1b
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/0f8e5c86-0a8f-4268-a7c8-4170242504ae)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8e18f63a-e6d8-4cb9-9033-d5a99216720c)


**Create security groups:**

    -A)Internet-Facing-LB-SG
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8a3f950e-f57d-418b-aa1d-2c10556ce099)
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/6bfec826-7156-4ee4-83d8-3d8214139bbf)

    -B) Web-tier-SG
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/7c21f95d-9ff2-442f-bbe8-dc7ba1414bf2)
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/73e66231-5647-40b3-b78e-d941c5d0677a)

    -C) Internal Load balancer Security Group
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/3b80e73a-00d7-499f-9ddb-787a49a94ba8)
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/3c704717-e72f-40b2-a0c3-45cfc73a7f77)

    -D)Private instance Security Group
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/0e01f7ce-d18d-4030-b577-fd1ead060a5e)
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/20b39552-ddca-444b-8f47-022b9bd2fd90)

    -E) Database Security group
    ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/e4fa72d3-6679-4983-a143-633ba2a4a7a0)

**Part 2: Database Deployment**
     This section of the workshop will walk us through deploying the database layer of the three-tier architecture.

     Objectives:
      Deploy Database Layer
      Subnet Groups
      Multi-AZ Database

      A) creating subnet group in rds Section
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8944cf8d-7f48-40a4-be23-77b0419c84ab)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/3e23f5c7-51e6-450a-ab67-a5164889829b)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/bb0945e5-28bd-44a6-89c2-c6122982ad09)


      B) Create Database: 
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/6f46fdf3-5e5c-42d1-8b7e-8c2d5eca7c14)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/87e3909a-656d-4718-8cac-9cab9fa90af4)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/21896f95-fb09-49e1-ade3-a4b677f109eb)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/b083731d-4c3a-4955-ae6e-f34ed3a50e18)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/680500ca-f5cd-4469-9fd6-62926409eeeb)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/4700b34a-cdc7-49a2-8c48-07552fe67d81)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/092f30a1-f5cd-4dcc-b3cc-b10094db18b2)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8ea41f25-bcce-49a0-980f-3628e997d7a6)
      ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/9e561139-c61b-4624-bed0-bc6284c95c30)

**Part 3: App Tier Instance Deployment**

In this section, we are going to create an EC2 instance for our app layer and make all the essential software configurations so that the app can run correctly. The app layer will consist of a Node.js application running on port 4000. In addition, we will configure our database with some data and tables.

**Objectives:**
Create App Tier Instance
Configure Software Stack
Configure Database Schema
Test DB connectivity


**App Instance Deployment** 
Let’s name our app instance ‘app-web-tier’ for the three-tier architecture and select the Amazon Linux 2 AMI for our application and operating system image.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/46c7c96f-e74b-4e36-9301-808d194293c0)

We’ll be using the free tier eligible T.2 micro instance type so let’s select that to proceed.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/9562f3b2-9e2a-4f12-8b83-5895a05d3817)


Even though ‘Proceed without a key is (Not recommended)’, we’ll proceed without a key pair for architecture.
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8e3bbe43-280f-4e6c-aa21-050e89763fcf)


Earlier we created a security group for our private app layer instances, so go ahead and select that along with our default VPC and the ‘private-app-subnet-az-1' under Network settings.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/778def9c-5461-486c-97af-9e3384f25560)

The ‘appLayer’ instance is created. Now, let’s navigate back to the Instance dashboard of the EC2, select the ‘appLayer’ instance, click on Actions, and then Modify IAM role under Security to update the IAM role.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/c606136f-dcb8-4c31-a9db-72e6ac980403)


Select the IAM role we created earlier from the ‘IAM role’ list and click ‘Update IAM role’ to update the role.
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/3f1c8626-9a0e-4cc9-afa4-3446d637da34)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/7d009428-c75f-46a4-9aaa-587569b7aac7)


Connect to Instance
Let’s navigate to our list of running EC2 Instances by clicking on Instances on the left-hand side of the EC2 dashboard. When the instance state is running, connect to the instance by clicking the checkmark box to the left of the instance and clicking the connect button on the top right corner of the dashboard. Select the Session Manager tab, and click Connect. This will open a new browser tab for you.

**NOTE**: If you get a message saying that you cannot connect via session manager, then check that your instances can route to your NAT gateways and verify that you gave the necessary permissions on the IAM role for the Ec2 instance.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/2a2e081d-24be-4b53-bb46-37368a87cc0d)

When you first connect to your instance like this, you will be logged in as ssm-user which is the default user as indicated below.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/00597ca0-a4e7-4990-ab4f-829b976377b6)

Let’s take this moment to make sure that we are able to reach the internet via our NAT gateways. If our network is configured correctly up till this point, we should be able to ping the Google DNS servers:
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/08fa4350-236c-4a0a-a206-63bd22a84763)

Transmission of packets from our ping command means that we’re successfully connected to the internet. Congratulations and give yourself a pat on the back. You did! :)

You can stop the ping by pressing ctrl + c.

NOTE: If you can’t reach the internet then you need to double-check the route tables and subnet associations to verify if traffic is being routed to your NAT gateway!

Configure Database
Let’s start this process by downloading the MySQL CLI using the ‘sudo’ command below.
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/af65741a-c847-4d32-87c5-1524b136d2d2)

Now, let’s initiate our DB connection with our Aurora RDS writer endpoint. In the following command, replace the RDS writer endpoint and the username, and then execute it in the browser terminal:

We successfully connected to the database after replacing the database endpoint name (database-1.cluster-czkx0xyclbd4.us-east-1.rds.amazonaws.com), the username (admin), and typing in the password as indicated in the above image.

NOTE: If you cannot reach your database, check your credentials and security groups then try again.

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/f8fe10b8-1fa2-4359-8149-0142fc0d77e7)

- CREATE DATABASE webappdb;

Let’s verify that the database was created correctly with the following command:
Now that we’ve successfully connected to MySQL database, let’s create a database called ‘webappdb’ with the following command using the MySQL CLI:
- SHOW DATABASES;
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/c78bbd3b-a307-4a76-84d2-0919642998c3)

Now, let’s create a data table by first navigating to the database we just created with the command below:
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/1c99c1a2-0c49-439e-8510-53bbe40586f3)

Let’s verify if the tables were created with the below command:
- show tables;
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/272bd1af-0b48-4e06-bac8-23a549ae0397)

The tables were successfully created as illustrated in the above image.

Now that we have the tables created, let’s insert data into the table with the command below for use/testing later:
- INSERT INTO transactions (amount,description) VALUES ('400','groceries');

Let’s verify that our data was added by executing the following command:
- SELECT * FROM transactions;
 ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/bdb58f66-fefe-4530-9725-e11bbddc8ed9)


**Go to your created s3 bucket: (asd-3-tier-bucket) **
- upload given three-app-tier github project files and folders
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/6d5cc859-f401-469e-a845-77e19e429544)



**Configure App Instance**
The first thing we will do is update our database credentials for the app tier. To do this, let’s open the application-code/app-tier/DbConfig.js file from the GitHub repo in a text editor on the local computer.

-to get s3 bucket uploaded folders and file we need to install  aws-cli in private instance
-sudo yum install aws-cli
- then get s3 bucket data in private instance using below command
   -aws s3 ls
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/8dfe154f-1896-4eb7-b0c6-cd0405a0a895)

-now do configuration add 
  -RDS-endpoint
  -Username
  -Password
  -Database name
  
  in DbConfig.js file which is inside three-tier-project/app-tier/DbConfig.js 
  -and upload only DbConfig.js file in s3 bucket inside app-tier folder so you will get latest changes
  ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/ce347742-aa7a-43f9-8dd8-fc59b5a76e73)

-With the ‘app-tier’ folder and contents uploaded to the S3 bucket, let’s go back to our SSM session via our EC2 ‘appLayer’ instance to install all of the necessary components to run our backend application. Start by installing NVM (node version manager) using the command below:

-curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
-source ~/.bashrc

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/f62aa623-da6b-427f-9afa-3e1d5f1958b0)

-Next, let’s install a compatible version of Node.js and make sure it’s being used with the below commands:
- nvm install 16
- nvm use 16

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/0c3221f9-1603-48b3-81cb-30b4c785d7c0)

-PM2 is a daemon process manager that will keep our node.js app running when we exit the instance or if it is rebooted. Let’s install that as well.
  - npm install -g pm2

-Now, we need to download our code from our S3 buckets onto our instance. With the command below, let’s replace BUCKET_NAME with the name of the bucket we uploaded the app-tier folder to:

   - aws s3 cp s3://BUCKET_NAME/app-tier/ app-tier --recursive
     Ex. (aws s3 cp s3://asd-3-tier-bucket/app-tier/ app-tier --recursive)

     ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/4d0d77d1-86c2-47ab-94ed-75c3890dff5b)

-Next, navigate to the app directory, install dependencies, and start the app with pm2 with the command below:
  - cd ~/app-tier
  - npm install
  - pm2 start index.js

![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/94b7f552-204c-43de-a3fc-db5666785b63)
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/86f6a910-767a-470f-be62-abc50e8aa774)

-To make sure the app is running correctly run the following:
    -pm2 list

-The app is running. If you see an error, then you need to do some troubleshooting. To look at the latest errors, use this command:
   -pm2 logs
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/1cdf1fa0-8e36-4c30-98ae-31b978e0cd89)
 
   You can check to see if there’re errors in the app logs by executing the ‘pm2 log's command.

  You can also see that the AB3 backend app is listening at http://localhost:4000.

NOTE: If you’re having issues, check your configuration file for any typos, and double-check that you have followed all installation commands recommended till now.

-PM2 will make sure our app stays running when we leave the SSM session. However, if the server is interrupted for some reason, we still want the app to start and keep running. This is also important for the AMI we will create so let’s keep PM2 running by executing the command below:

  - pm2 startup

-The below message appears on the command prompt above after running the ‘pm2 startup’ command.
 [PM2] To setup the Startup Script, copy/paste the following command: 
 
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/125cbb0c-5876-4445-ab62-39ca4f57008b)

   -pm -save
   ![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/63f51634-9756-4b2a-98e6-70c4f3caf7aa)

-Test App Tier
Now let’s run a couple tests to see if our app is configured correctly and can retrieve data from the database.

To check out our health check endpoint, copy this command into your SSM terminal. This is our simple health check endpoint that tells us if the app is simply running.

- sudo curl http://localhost:4000/health
- curl http://localhost:4000/transaction
![image](https://github.com/asdweb22/Aws-three-tier-architecture/assets/62742174/1532122a-a3a0-4804-b1c7-6c3671b51db4)

-The two above responses indicate that our networking, security, database, and app configurations are correct. Our app layer is fully configured and ready to go.
