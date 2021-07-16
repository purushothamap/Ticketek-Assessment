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



After successful build, i have configured 
