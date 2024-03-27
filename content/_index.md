---
title : "Building a Simple AWS CloudTrail Data Analytics Solution"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Building a Simple AWS CloudTrail Data Analytics Solution

#### Overview

The demo will show how you can visualize AWS CloudTrail data in Amazon QuickSight and start building simple security dashboards. Although CloudTrail is enabled by default in every AWS Account, Kathy (me) will configure a new trail, and also to show where CloudTrail configurations are made.

After configuring a new trail, I will add a new user into my AWS account (named dude-from-nowhere). I will then log in as that user and do some activity that simulates a user who is issuing application programming interface (API) calls. One of these API calls will (accidentally) turn off a web server. If you want to follow the exact instructions in your account, you can mimic the scenario that I has in this account before you enable CloudTrail. To do so, you can create an Amazon Elastic Compute Cloud (Amazon EC2) instance to function as the web server.

After I turns off the web server as the user `dude-from-nowhere`, I will log out and log in again as an administrator. I will then use CloudTrail data to investigate what happened by getting information, such as when the server was turned off. I will also discover the other API calls that the nicholas user made, because that account could have been compromised.

Here is the reference architect for this lab
![architect](/images/architect/lab-cloudtrail-architect.png)
#### Content

1. [Setting up AWS Config](1-setting-up-aws-config/)
2. [Working with AWS Config via CLI](2-utilize-aws-cli/)
3. [Checking S3 bucket](3-check-s3-bucket/)
4. [Resources Clean Up](4-clean-up)