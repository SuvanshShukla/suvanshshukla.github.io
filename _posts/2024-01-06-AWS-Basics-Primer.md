---
title: AWS Basics Primer
date: 2024-01-06
categories: [AWS, Tutorial]
tags: [aws, learning]
---

I was having a conversation with a good friend (shout out to DLV!) a couple of days ago and we were talking about different things to learn to up-skill ourselves and I suggested learning CI/CD via AWS. Later he asked me about how to learn CI/CD on AWS, so I thought I’d write a quick and rough guide.

By my understanding of CI/CD (which stands for Continuous Integration and Continuous Deployment), is that, if you have a website that you’re working on, you won’t finish the whole website and deploy it onto the internet all at once. Rather, what is more likely is that you’ll work on it part-by-part and slowly update it with new features that you’ve made and tested.

This process of slowly adding to the website is the core concept of CI/CD. This complete pathway or “pipeline” from making a change and seeing it in your deployed website is what we’re concerned with. This pipeline has three major components, namely the source, the build and the deploy.

All three stages have their equivalents in different platforms, but on AWS we have AWS Code Commit, AWS Code Build, and AWS Elastic Beanstalk. Together, all these phases/components make up an AWS Code Pipeline. This is the overview of a CI/CD pipeline no AWS.
A little bit about AWS Code Commit

This AWS service is analogous to GitHub and serves as a version control system for your code. For working with Code Commit you will need the AWS CLI. Code Commit has most GIT features that you might need to use for your project. The reason I’ve mentioned Code Commit as the source is because it provides a more cohesive experience when working with other AWS service. It should be noted that you can use a GitHub repo or a GitLab repo as the source in your AWS Code Pipeline too. You can even migrate your code to AWS Code Commit from GitHub (but how to do that is beyond the scope of this article)
A little bit about AWS Code Build

This AWS service is where our program/application is built and we get the artifact that will be deployed onto the server in the deploy stage.This stage compiles our code. This stage compiles our code, downloads the required dependencies and runs our written test cases. To do this we need to set up an appropriate environment and thus requires computational resources.
A little bit about AWS Elastic Beanstalk

AWS Elastic Beanstalk is the platform onto which we deploy our generated artifact. AWS elastic beanstalk has multiple different parts to it and encompasses the EC2 instance which is the running machine with out application. A great thing about EBS is that it automatically shrinks and stretches it’s resources based on the usage of our website. EC2 or Elastic Cloud Compute can be thought of as the computer which houses our running application, and it is this that we SSH into when we want to directly interact with our running server.
A
little bit about AWS Code Pipeline

AWS Code Pipeline is the AWS service that basically integrates and combines all the above mentioned services and gives us a working CI/CD pipeline. All the above components can be set-up when creating a Code Pipeline. It allows for very specific control over the complete CI/CD flow and can be set up to work with different service.
Other notable features of AWS

AWS has a lot of features that simply can’t be addressed in one post. But here’s a few other things that you might have to interact with when working with AWS :

    IAM: This is the identity management service that AWS has that allows users to give other users access to certain features and parts of the project. You’ll will need this when dealing with multiple users and supplying them with appropriate privileges.
    VPCs — This is the virtual private cloud where all the different components of AWS created/defined in. This basically means that your AWS Code Commit repository, Code Build project and Elasticbeanstalk instances will all be on the same VPC by default. This is set-up primarily for convenience and safety. I suggest reading more on this as this is something you might need to fiddle around with to get things to interact with each other.

It should be no surprise that while AWS provides all these service, they are not technically free. You do need to provide some financial details (credit/debit card details) when creating an AWS account. So when you first signup, AWS will charge a very minimal fee to test your entered details.

Here’s some more info on the pricing of various AWS services :

    Elastic Beanstalk : There is no additional charge for AWS Elastic Beanstalk. You pay for AWS resources (e.g. EC2 instances or S3 buckets) you create to store and run your application. You only pay for what you use, as you use it; there are no minimum fees and no upfront commitments.
    AWS Code Commit : always free but only for 5 active users per month (this includes IAM and root users) [LINK]
    AWS Code Build : always free but only for 100 build minutes per month [LINK]
    AWS Code Pipeline : always free but only for one active pipeline per month [LINK]
    Amazon EC2 : 12-months free but only upto 750 Hours per month [LINK]
    more readable and beginner friendly link on what is AWS free tier

I understand that I have not gone in depth about each separate service, but I will try writing about all the other services in other posts. Meanwhile here are some resources for learning CI/CD and AWS services :

    Introduction to AWS Code Commit: Setting Up Permissions
    Introduction to AWS Code Commit: Creating a Repo
    Great Video on setting up CI/CD pipeline on AWS by JavaTechie
    Deploying an application on AWS by JavaTechie