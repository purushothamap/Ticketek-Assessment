# Ticketek-Assessment

After thoroughly going through the requirement, I understood that AWS Elastic Beanstalk is right fit to deploy this solution.
Actually there are few advantages to deploy applications on elastic beanstalk, especially Microsoft .NET applications.

•	Automated security Patching

•	Install custom software if needed.

•	Windows instances can be domain joined.

•	High availability with autoscaling, load balancing and SSL.

•	Simple one step deployment from Visual Studio with AWS Toolkit for VS.


Post cloning solution repository on my local from https://github.com/opserver/Opserver, the solution has been built using visualstudio 2019. Since it is being deployed into Elastic Beanstalk, the solution configuration is set as "Release", so that all dependency libraries pull into single deployable package.

We have feature in Visual Studio to deploy .Net applications directly into AWS Elastic Beanstalk, "AWS Toolkit for Visual Studio" is a plugin to the Visual Studio IDE. With the toolkit you can deploy and manage applications in Elastic Beanstalk while you are working in your Visual Studio environment.

Firstly, we need to create a new environment and deploy your application.

1. In Solution Explorer, right click on "Opserver" project, and then select Publish to AWS Elastic Beanstalk.
2. In the Publish to AWS Elastic Beanstalk wizard, enter your account information.
3. Actually AWS Elastic Beanstalk wizard didn't allow me to add AWS credentials, so found another approach to add the credentials.
4. Go to "view" tab on visual studio, and then select "AWS Explorer", it would ask "Access key ID" and "Secret access key".
    
    ![image](https://user-images.githubusercontent.com/53302261/125888117-8216a213-e943-49ac-a01f-4a0b1bd57c3b.png)

5. To generate "Access key ID" and "Secret access key", i have logged into AWS Account and then open IAM console.
    
    On the navigation menu, choose Users and then i have selected "Puru Pendyala" user.
    Open the Security credentials tab, and then choose Create access key.
    To see the new access key, choose Show.
    choose Download .csv file. Store the .csv file with keys in a secure location.
    
6. Enter above credentials when "New Account Profile" dialog box opens.
    ![image](https://user-images.githubusercontent.com/53302261/125888184-0d4bbd2d-862a-4495-8846-46ff93a7657f.png)
   
7. To create a credential profile, enter the following data into the dialog box and then choose OK.
    Profile Name
        (Required) The profile's display name.

    Storage Location
        (Required) Choose whether to use the SDK Credential Store or the shared AWS credentials file.

    Access Key ID
        (Required) The access key ID.

    Secret Access Key
        (Required) The secret access key.

    Region
        (Required) The default AWS Region that you want to associate this profile with.
        

8. Once profile has been created, it will automatically display when you right click on Project select Publish to AWS Elastic Beanstalk" option.
    ![image](https://user-images.githubusercontent.com/53302261/125889061-4b12e1c2-a9cb-4b7d-962d-de2900b83ecf.png)

9. Since we are creating new application environment, ensure that "Create a nwe application environment" should be selected.
10. Click "Next"
11. It would ask for Application, Environment and URL on Application Environment Wizard.
    ![image](https://user-images.githubusercontent.com/53302261/125889358-01f311ec-ca84-40fc-ae14-70301691557b.png)
12. Click "Next"
13. And then it would ask Amazon EC2 Lauch configuration, like OS, instance type, AMI and Load Balancer etc. Select relavent options based on application capacity and usage.  Since is test environment, i have selected with minimal options.
    ![image](https://user-images.githubusercontent.com/53302261/125889948-98dc2566-f7d6-4013-87cc-f4319f931cf7.png)
14. Click "Next"
15. Select Permissions like Deploy application permission and Service Permission roles.
    ![image](https://user-images.githubusercontent.com/53302261/125891234-4f130aba-d59c-4b7d-8eee-464c1946eea9.png)

16. Select Build and IIS deployment settings
    ![image](https://user-images.githubusercontent.com/53302261/125891355-7c233a5a-28c9-4932-9d34-082b1606cc77.png)

17. On the next Wizard, review the options and select "Deploy".
    ![image](https://user-images.githubusercontent.com/53302261/125891429-0ad61a42-b267-4a0a-9718-824ea18e3da6.png)

18. Basically this process will create environment in AWS Elastic Beanstalk with following resources provisioned.
     •	AWS Elastic Beanstalk will automatically create S3 bucket to store environment Data. 
     
     •	Create security groups which allows only https port for all EC2 instances.
     
     •	Create autoscaling lauch configuration and scaling group.
     
     •	Launch EC2 instances.
     
     •	Create autoscaling group policies.
     
     •	Add EC2 instances to Autoscaling group.
     
     •	Create cloudwatch alarm for all EC2 instances.
     
     •	Create Load Balancer and add EC2 instances into it.
     
     •	Start application update on all EC2 instances.
     
     •	Once all resources provisioned above, the status will update in Visual Studio as "Environment healthy" .


19. Once environment is healthy, You can monitor the resources from Visual studio.
    ![image](https://user-images.githubusercontent.com/53302261/126067802-e9836d01-7c7c-4ddd-9503-05931e2a51c8.png)

20. You can also setup cloudwatch dashboard to monitor the resources directly from AWS Console.
    ![image](https://user-images.githubusercontent.com/53302261/126067846-68f085c6-f852-4562-bad2-90a1e1290a55.png)

21. EC2 instance types and AMI can still be modified even after provisioning the environment.
22. You can also set the notifications on the environment status.
23. You can also update advanced configuration details from visual studio related to autoscaling and load balacing properties.
    ![image](https://user-images.githubusercontent.com/53302261/126067950-635d7b91-8181-422c-bb44-ced37efab79f.png)

24. Snapshot logs can also be monitored without login to AWS Console from Visual studio.
    ![image](https://user-images.githubusercontent.com/53302261/126067996-556aab64-2fcc-4823-996c-77d969f96009.png)


The application cane be accessible from http://ticketek-dev.ap-southeast-2.elasticbeanstalk.com/, but it has some issues with respect to code, so couldn't load the GUI. Need additional efforts to verify and fix the issue.
