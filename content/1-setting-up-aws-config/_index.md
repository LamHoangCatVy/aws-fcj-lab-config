---
title : "Setting up AWS Config"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 1. </b> "
---


After singing in to the console, search for Config, then navigate to AWS Config

![Console -> AWS Config](/workshop3/01.png)


In the AWS Config dashboard page, click `Get started`

![AWS Config dashboard page](/workshop3/02.png)

In the `Recoding method` panel -> `Recoding strategy` -> Choose `Specific resource types`
In the Data governance -> Choose `Create AWS Config service-linked role`

![Settings](/workshop3/03.png)

In the `Delivery method`
- Choose `Create a bucket`
- Leave the `S3 Bucket name` field as default, AWS will help you create a new bucket in S3 services. We will use this name to make the "skeleton" for our configuration.
- Check the box "Stream configuration changes and notifications to an Amazon SNS topic"
- Choose `Create a topic`
- Specify the SNS topic name `awsconfig-lab`
- Choose `Next`

![Delivery](/workshop3/04.png)

In some cases, you can use the AWS Managed Rules to fit your business needs. In this lab, leave it as default, scroll down and click `Next`.

![Rules page](/workshop3/05.png)

Review and click `Confirm`.

![Review page](/workshop3/06.png)