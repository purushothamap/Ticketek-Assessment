# Ticketek-Assessment

After thoroughly going through the requirement, I understood that AWS Elastic Beanstalk is right fit to deploy this solution.
Actually there are few advantages to deploy applications on elastic beanstalk, especially Microsoft .NET applications.

•	Automated security Patching

•	Install custom software if needed.

•	Windows instances can be domain joined.

•	High availability with autoscaling, load balancing and SSL.

•	Simple one step deployment from Visual Studio with AWS Toolkit for VS.


Post cloning solution repository on my local from https://github.com/opserver/Opserver, the solution has been built using visualstudio 2019. Since it is being deployed into Elastic Beanstalk, the solution configuration is set as "Release", so that all dependency libraries pull into single deployable package.

We have feature in Visual Studio to deploy .Net applications directly into AWS Elastic Beanstalk, AWS Toolkit for Visual Studio is a plugin to the Visual Studio IDE. With the toolkit you can deploy and manage applications in Elastic Beanstalk while you are working in your Visual Studio environment.

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
        

After successful build, i have configured 
