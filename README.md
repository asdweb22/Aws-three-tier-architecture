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
