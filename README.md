# Security-and-Identity-Management-IAM 

Security and Identity Management (IAM) typically refers to the processes, tools, and policies used to manage digital identities and control user access to resources in an organization. Here's a breakdown of the key concepts and components. 

## Introduction to Cloud Computing - Security and Identity Management (IAM) 

This mini project is designed to guide through the intricacies of Amazon Web Services (AWS), specifically focusing on Identity and Access Management (IAM). 
Before diving into the specifics of IAM, it's crucial to establish that a basic understanding of cloud computing priciples ia s prerequisites for the project. 

As a recap, it involves delivering computing services over the internet, including servers, storage, databases, networking, software, analytics, and intelligence, to offer faster innovation, flexible resources, and economies of scale. 

In this project we will be working with hypothetical fintech startup named **Zappy e-Bank**. This fictitiuos company represents a typical startup venturing into financial technology sector, aiming to leverage the cloud's power to innovate scale, and deliver finacial services. The scenerio is set up to provide a realistic backdrop that will help you understand the application of **AWS IAM** in managing cloud resources securely and efficiently. 

## The Importance of IAM Zappy e-Bank 

For Zappy e-Bank, like any company dealing with financial services, security and compliance are paramount. The company must ensure that its data, including sensitive customer information is securely managed and that access to resources is tightly controlled. AWS IAM plays a critical role in achieving these security objectives by allowing the company to define who is authenticated **(signed in)** and authorised **(has permission)** to use a resources. 

## IAM will Enable Zappy e-Bank to: 

- Create and manage AWS users and groups, to control access to AWS services and resources securely. 

- Use Identity and Access Management (IAM) roles and policies to set more granular permissions for AWS services and external users or services that need to access Zappy e-Bank AWS resources. 

- Implement strong access controls, including multi-factor authentication (MFA), to enhance security. 

 This project will based on setting up IAM for **Zappy e-Bank**, creatinga secure environment that reflects real-world usage and challenges. Through the hands on experience, the fundamentals of IAM will be learnt, how to mange access to AWS resources, and best practices for securing your cloud environment. 

 ## Project Goals

 To understand and implement the core principles of cloud security and Identity and Access Management (IAM) in a cloud computing environment, focusing on user identity, access control, and resource protection using real-world cloud platforms. 

## Project Setup 
1. Log into the AWS Management Console: Use your administrative account to log in. 

2. Navigate to the IAM Dashboard: Here, you'll manage users, groups, roles, and policies. 

## Exerxises:

## Creating IAM Users

An IAM user ia s unique identity within an AWS account that represents a person or service, granting specific permission to access and interact with AWS resources under controlled and customizable security policies. 

Imagine that you have a big, secure building **(AWS account)** that you own and control. When you first get the key to this building, you're given a master key **(root user)** that can open every door, access every floor, and make changes to the building's structure itself.

This master key is powerful, allowing you to do anything from adding new rooms (services) to changing the locks (security settngs). Also because the key can do so much, it's risky to use for daily tasks like if you lost it, so if found someone could do anything they want with your building. 

Now, imagine you have specific tasks that need to be done in the building, like cleaning, maintenance or security checks. You wouldn't give out the master key to every person who needs to do those jobs. Instead you create specific keys (IAM users) that can only open certain floors. These keys are less powerful but much safer to use for everyday tasks. They ensure that the people holding them can only access the parts of the building they need to do their jobs and nothing more.

Let's set up IAM usesr for a backend development, **John** and a data analyst, **Mary**, by first determining their specific access needs.

As a backend developer, John requires access to servers **(EC2)** to run his code, necessitating an IAM user with policies granting EC2 access.

As a data analyst, Mary needs access to data storage **(AWS S3 service)**, so her IAM user should have policies enabling S3 access.

Considering **Zappy e-Bank's** plan to expand its team with 10 more developers and 5 additional data analyst in the coming months, its inefficient to individually create similar policies for each new member. A more streamline approach involves:

1. Crafting a single policy tailored to each roles's access requirements.

2. Associateing this policy with a group specifically designed for that role.

3. Adding all engineers or analysts to their respective groups, simplying the management of permission and ensuring consistent access accross the team. 

Creating IAM User
An IAM user in AWS (Identity and Access Management) is an entity you create within your AWS account that represents a person or an application that needs to interact with AWS resources.
Think of it as a specific identity with its own set of credentials (like a username and password for console access, or access keys for programmatic/API access). By default, a newly created IAM user has no permissions to do anything in AWS. You then attach policies to this user (directly or via groups) to grant them specific permissions to perform actions on your AWS resources. 

![IAM Console Home](./img/01.%20IAM%20Console%20Home.png)

## Create Policy for the Development Team

1. In the IAM console dashboard, click policies

![IAM Dashboard](./img/02.%20IAM%20Dashboard.png) 

2. Click create policy

![Create Policy](./img/03.%20Create%20Policy.png) 

3. In the select a service section, search for ec2 

![Select Service](./img/04.%20Select%20Service.png) 

4. For simplicity sake select **"(All EC2 actions)"** checkbox 

![Select All EC2 Actions](./img/05.%20Select%20All%20EC2%20Actions.png) 

5. Also, make sure scroll down on the page to select **"(All)"** in the Resources section 

![Select All in Resources Section](./img/06.%20Select%20All%20in%20Resources%20Section.png) 

6. Click next 

![Click Next](./img/07.%20Click%20Next.png) 

7. Provide the name **developers** and description for the policy and click create policy 

![Successfully Create Developers Policy](./img/08.%20Successfully%20Create%20Developers%20Policy.png) 

Notice that after creating the policy, if you search for **"developers"** in the search box, you will notice that a number of policies are returned. This highlights the presence of both AWS managed and customer managed policies. **AWS managed policies** are predefined by AWS and provide permissions for many common use cases, allowing for quick and broad access management accross AWS servicee with the need for custom policy creation like we just did. in contrast, customer managed policies are created and fully controlled by customer, allowing for more tailored, specific access controls that can be finely tuned to organisationrequirements. 

![Customer Managed Policy](./img/09.%20Customer%20Managed%20Policy.png) 

## Create Policy for the Data Analyst

Repeat the process above for the Data Analysts team, but instead of **EC2** search for **S3**. Also name the policy **analysts** instead of **developers** give description of your choice. 

![Successfully Create Analysts Policy](./img/10.%20Successfully%20Created%20Analysts%20Policy.png) 

## Create Group for the Development Team 

1. In the IAM console navigation, select **User group** and in the top right click **Create group** 

![Create Development User Group](./img/11.%20Create%20Development%20User%20Group.png) 

2. Provide a name for the group 

![Name the Group](./img/12.%20Name%20the%20Group.png) 

3. Attach the  developer policy created ealier to the group. This will allow any user in the **DEvelopment-Team** group to have access to EC2 instances alone

![Attached the Policy](./img/13%20Attach%20the%20Policy.png) 

4. A group for development was created successfully and EC2 permission policy was attached. 

![Create Development Group Successfully](./img/14.%20Create%20Development%20Group%20Successfully.png) 

## Create Group for the Data Analysts Team 

The same process should be repeated for Data Analysts team. 

-  The Group name should be Analysts-Team 

- Instead of attaching developers policy, attach analyst policy. 

![Create Analysts Group Successfully](./img/15.%20Create%20Analysts%20Group%20Successfully%20.png) 

## Create IAM User for John 

Let's recall that John is a backend developer, therefore he need to be added as a user to the **Develoment-Team** group 

- Navigate to the IAM dashboard again, select "Users" and the click "Create user". 

![Create IAM User for John](./img/16.%20Create%20Users.png) 

- Review the highlights in the images 
    
    - Provide the name of the user. In this case "John" 

    - Ensure that the user can access the AWS Management Console. If this is not selected, the user will not be able to login from web browser.

![User Name and Click AWS Console](./img/17.%20User%20Name%20and%20Click%20AWS%20Console.png)  

- Permissions: Add John to the development team group.

![Permission Checked](./img/18.%20Permission%20Checked.png)

- Click on **create user** 

![Click Create User](./img/19.%20Click%20Create%20User.png) 

- Download the login credentials for John

![John Login Credentials](./img/20.%20John%20Login%20Credentials%20.png)

![John Login Credentials Cont.](./img/21.%20John%20Login%20Credentials%20Cont..png) 

## Creating IAM User for Mary

Repeat the same step for Mary. But recall that Mary is a data analyst, which means she need to be added to **Analysts-Team** group 

![Mary Login Credentials](./img/22.%20Mary%20Login%20Credential.png) 

## Testing asn Validation 

## Testing John's Access 

Login as John: Use the credentials provided to John to log into AWS Management Console. This simulates John's user experience and ensures he has the correct access. 

- John has correct access but prompted to change password. 

![Testing John' Access](./img/23.%20Testing%20John'%20Access.png) 

![John Successfully Change Password](./img/24.%20John%20Successfully%20Change%20Password.png) 

**Access EC2 Dashboard:** Navigate to the EC2 dashboard within the AWS Management Console. John should be able to view, launch, and manage  EC2 instance as the role requires access to servers for deploying and managing backend applications

![EC2 Instance Dashboard](./img/25.%20EC2%20Instance%20Dashboard.png)

![EC2 Instance Launch](./img/26.%20EC2%20Instance%20Launch.png)

**Perform EC2 Actions:** Attempt to create a new EC2 instance or modify an existing one to confirm that John has the necessary permissions. If John can succsessfully perform these actions, it indicates his IAM user has been correctly set up with the appropriate policies for a backend developer.

![Launching an Instance](./img/27.%20Launching%20an%20Instance.png)

![Successfully Launch](./img/28.%20Successfully%20Launch.png)

**Testing Mary's Access** 

Login as Mary: Use the credentials provided to Mary to log into the AWS Management Console. This ensures that Mary's user experience is as expected and she has the correct access. 

![Mary Successfully Change Password](./img/29.%20Mary%20Successfully%20Change%20Password.png) 

**Access EC2 Dashboard:** Navigate to the S3 dashboard within the AWS Management Console. Mary should be able to view, create, and manage S3 buckets  as the role requires access to data storage for analysing and managing data.

![Mary Console Home](./img/30.%20Mary%20Console%20Home.png)

**Perform S3 Actions:** Attempt t0 create a new S3 buckets or upload data to an existing one to verify that Mary has the necessary permissions. Succsessfully execution of these tasks will confirm that Mary's , IAM user has been correctly set up with the appropriate policies for the data analyst.

![Mary Create S3 Bucket](./img/31.%20Mary%20Create%20S3%20Bucket.png) 

![Marry Successfully Create Bucket](./img/32.%20Mary%20Successfully%20Create%20Bucket.png)

## Validating Group Policies 

For both users, ensures that their access is confined to their role-specific resources (EC2 for John and S3 for Mary) and that they cannot access other AWS services beyond what their group policies permit.

- John failed to create S3 bucket since it has no permission

![John Failed to Create S3](./img/33.%20John%20Failed%20to%20Create%20S3.png) 

- Mary failed to launch instance 

![](./img/34.%20Mary%20Failed%20to%20Launch%20Instance.png)

## Implement Multi-Factor Authentication (MFA) 

With the newly created users. Let's create Multi-Factor authentication for John. 

Multi-Factor Authentication (MFA) is a security features that adds an extra layer of protection to your AWS account and resources. With MFA enabled, users are required to provide two or more forms of authentication before they can access AWS resources. 

John, the backend developer, logs into the AWS Management Console to access EC2 instance for deploying and testing his code. 

When John attempts to log in, after providing his username and password, AWS prompts him to enter a one-time code generated by a MFA device.

## Setting Up MFA for John 

1. Click on **User** and then click on John. It is assumed we already created a user account for John

![Click Users](./img/35.%20Click%20Users.png) 

![Click John](./img/36.%20Click%20John.png)

2. Click on enable MFA as shown in the image below 

![Assign MFA Device](./img/37.%20Assign%20MFA%20Device.png) 

3. Enter a device name for John MFA and select authenticator app 

![Enter Name and Select Authenticator App](./img/38.%20Enter%20Name%20and%20Select%20Authenticator%20App.png)

**Note:** You should install authenticator app like **Google authenticator** or **microsoft authenticator** on your mobile device if you don't have it installed

4. Click next 

5. Open **Google authenticator** or **microsoft authenticator** application on your mobile device to scan th QR Code, then you fill in the 2 consecutive codes as shown in the image below 

![John Scan QR Code](./img/39.%20John%20Scan%20QR%20Code.png)

6. By completing step 1-5, MFA will be enabled for John

![John Successfully Enable MFA](./img/40.%20John%20Successfully%20Enable%20MFA.png) 

## Setting Up MFA for Mary 

Repeat the same step for Mary. 

1. Click on **User** and then click on Mary. It is assumed we already created a user account for Mary 

![Click Users and Click Mary](./img/41.%20Click%20Users%20and%20Click%20Mary.png) 

2. Click on enable MFA as shown in the image below for Mary

![Assign MFA Device for Mary](./img/42.%20Assign%20MFA%20Device%20for%20Mary.png) 

3. Open **Google authenticator** or **microsoft authenticator** application on your mobile device to scan th QR Code, then you fill in the 2 consecutive codes as shown in the image below 

![Mary QR Code](./img/43.%20Mary%20QR%20Code.png) 

4. By completing step 1-5, MFA will be enabled for Mary

![Mary Succcessfully Enable MFA](./img/44.%20Mary%20Successfully%20Enable%20MFA.png)


## Project Reflection

1. **Explain the Role of IAM in AWS:** AWS Identity and Access Management (IAM) enables secure management of users, roles, and permissions, allowing administrators to control who can access specific AWS resources and what actions they can perform, thereby ensuring security and efficient resource management in the cloud.

2. **Differentiate Between IAM Users and Groups:** IAM users are individual identities with specific credentials and permissions, while IAM groups are collections of users that share common permissions through attached policies, simplifying permission management.

3. **Describe the Process of Creating IAM Policies:** To create a custom IAM policy, define the required permissions using a JSON policy document, review and validate it, save the policy, and then attach it to relevant users, groups, or roles to grant specific access as per organizational requirements.

4. **Explain the Significance of the Principle of Least Privilege:** The principle of least privilege in AWS IAM ensures that users and services are granted only the minimum permissions necessary to perform their tasks, reducing the risk of accidental or malicious misuse of resources.

5. **Reflect on the Scenario with John and Mary:** John was assigned to a "BackendDevelopers" IAM group with a custom policy granting access to Lambda and DynamoDB, while Mary was added to a "DataAnalysts" group with permissions restricted to S3 read-only access and Athena query execution.
