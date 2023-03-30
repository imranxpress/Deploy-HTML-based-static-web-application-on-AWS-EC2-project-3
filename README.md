# Deploy-HTML-based-static-web-application-on-AWS-EC2-project-3



## Table of Contents

   1. Goal
   2. Pre-Requisites
   3. Pre-Deployment
   4. Deployment
   5. Post-Deployment
   6. Validation

![aws3](https://user-images.githubusercontent.com/47071968/228753546-78d07ac2-5761-4fac-88d2-a96c21dcde66.png)

## Goal

Deploy HTML based static website on Amazon EC2 instance and configure logging, monitoring, alerts.  This project hosting static web application on Apache Web Server to serve the web pages to internet clients. 

## Pre-Requisites

    1. You must be having an AWS account to create infrastructure resources on AWS cloud.
    2. Source Code

## Pre-Deployment

Customize the application dependencies mentioned below on AWS EC2 instance and create the Golden AMI.

    1. AWS CLI
    2. Install Apache Web Server
    3. Install Git
    4. Configure Apache to start automatically after the instance reboot.


## Deployment

Infrastructure Setup:


    1. Create Security Group allowing port 22 from custom IP source ( Your workstation IP ) and port 80 from public.
    2. Create Key-Pair and download the private key.
    3. Create t2.micro type EC2 instance using Golden AMI. 
    4. Create Elastic IP and associate the IP to EC2 instance.
    5. Create GP2 type EBS volume named /dev/xvdb of size 5GB in same AZ where EC2 was created.
    6. Attach EBS volume to EC2 instance.
    7. Create Route53 hosted zone with your domain name and configure A record pointing to the EC2 EIP.
    8. Create private S3 bucket and enable versioning.


## Application Setup

    1. Create File System on xvdb volume and mount it on /var/www/html directory. 
    2. Use Git commands and clone the source code from Bit Bucket repository provided in the pre-requisites.  ()
    3. Deploy the source code into web server document root folder – /var/www/html
    
    
    
 ## Post-Deployment

    1. Configure Cloudwatch agent to monitor Memory utilization of EC2 instance.
    2. Create Cloudwatch Dashboard to monitor CPU & Memory metrics of the EC2 instance.
    3. Configure SNS topic and subscribe e-mail to the Topic.
    4. Configure Cloudwatch alarm with 1 data point and 5 minutes interval rate to notify to SNS topic when average CPU utilization is greater than 80% threshold.
    5. Configure Cloudwatch alarm with 1 data point and 5 minutes interval rate to notify to SNS topic when average Memory utilization is greater than 60% threshold. 
    6. Use AWS CLI commands to push webserver logs to S3 bucket.
    7. Configure S3 life cycle rules to transit previous version objects to Glacier after 30 days and delete the objects after 90 days of object creation date.

## Validation

    Verify if you are able to access the web application from internet browser. 
