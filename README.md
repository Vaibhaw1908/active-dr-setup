## Architecture Overview:

![image](https://github.com/user-attachments/assets/43ff7535-68aa-4654-918f-35ba8304ce8f)




#### 1. Here we have two Azure regions:
One is the Primary Region
The other is the Disaster Recovery (DR) Region
Both regions are active, which means they can handle traffic and serve users if one goes down.

#### 2. How the User will access:

A user/browser connects to a domain (website).
The request is routed through an API Gateway and Traffic Manager, which decides where to send traffic either primary or DR region.
Private DNS zone helps map names to the correct internal resources.

#### 3. Primary Region (left side):-

i) Virtual Network (VNet) and Subnets: They group and isolate resources securely.

ii) Firewall: Controls what gets in and out.

iii) Web App: Runs inside an App Service Plan with 3 instances in different Availability Zones (AZ 1, AZ 2, AZ 3) to ensure high availability. This ensures zone-level redundancy within each region.

iv) SQL Server & SQL Database: Also spread across 3 AZs and connected to the web app via a Private Endpoint for secure, private communication.

#### 4. DR Region:-
   
It has the same setup as the Primary Region, including VNet, Subnets, Firewall Web App and SQL services with 3 instances across different AZs. It also uses Private Endpoints to connect resources.
...


## Overview of DevOps architecture :

![image](https://github.com/user-attachments/assets/77810873-a5aa-4320-b73a-9a2f19ec6122)




#### 1. Change Commit
   
A developer/user commits code changes to a repository connected to Azure DevOps

#### 2. Azure DevOps triggers a Continuous Integration (CI) pipeline that:

i) Builds a Docker image of the application

ii) Pushes the image to Azure Container Registry (ACR)

#### 3. CD Pipeline - Deploy to Environments

A Continuous Deployment (CD) pipeline deploys the built image to:

i) DEV Environment → For initial integration testing

ii) TEST Environment → For QA/functional testing after validation in DEV

iii) PROD Environment → Final live deployment after user approval

#### Each environment contains:

Application Gateway – for routing and load balancing

App Service Plan – hosting the web application

Web Service – the actual deployed web app

SQL Database – backend database for data storage purpose



## Overview of Release Plan:-


![adsf drawio](https://github.com/user-attachments/assets/579d541a-f5e9-4469-8247-ee8947f189bb)





#### 1. Dev creates feature branch
   
A developer starts by creating a new branch to work on a specific feature or bug fix.

#### 2. Pull request created
   
Once the code is ready, a pull request (PR) is submitted for review.

#### 3. Code reviewed
   
The team reviews the PR to ensure quality, consistency, and functionality.

#### 4. Change checked into main branch
   
After approval, the changes are merged into the main branch.

#### 5. Pipeline triggered
    
A CI/CD pipeline automatically starts once the code is merged.

#### 6. Artifact packaged and deployed to test environment
    
The code is built, tested, and deployed to the test environment for validation by the QA team.

#### 7. Deploy to UAT (User Acceptance Testing)
    
After successful testing, the same artifact is promoted to the UAT environment for final approval by business users.
















