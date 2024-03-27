
---
title : "Working with AWS Config via CLI"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2. </b> "
---

Open Terminal on your own device, with AWS CLI v2 installed. Execute these commands:
- `mkdir aws-config-lab`: create a new foler.
- `cd aws-config-lab`: change directory to `aws-config-lab`.
- type `aws configure`: config your aws cli with your access and secret key (you can create one if you haven't had yet in `IAM Users`).

![CLI](/workshop3/07.png)

To verify that your configuration recorder has the settings that you want:

`aws configservice describe-configuration-recorders --region YOUR-REGION-CODE`

![CLI](/workshop3/13.png)

Check File delivery status. Mind the `configHistoryDeliveryInfo` (Enabled when you set up the configuration recorder.) & `configSnapshotDeliveryInfo`

`aws configservice describe-delivery-channel-status --region YOUR-REGION-CODE`

![CLI](/workshop3/14.png)

We will use AWS CLI `put-delivery-channel` to enable configuration snapshot.

First, create “skeleton” file `deliveryChannel.json` . Here we configure the frequency 1 hour

Note: Please create the file `deliveryChannel.json` in the `aws-config-lab` folder
![CLI](/workshop3/15.png)
![CLI](/workshop3/16.png)


```json
{
    "name": "default",
    "s3BucketName": "YOUR-S3-BUCKET-NAME",
    "snsTopicARN": "YOUR-SNS-TOPIC-ARN",
    "configSnapshotDeliveryProperties": {
        "deliveryFrequency": "One_Hour"
    }
}
```

![CLI](/workshop3/19.png)

<details>
<summary>You can follow these steps to copy your BucketName and snsTopicARN</summary>
![BucketName and snsTopicARN](/workshop3/08.png)
![BucketName and snsTopicARN](/workshop3/09.png)
![BucketName and snsTopicARN](/workshop3/10.png)
![BucketName and snsTopicARN](/workshop3/11.png)
![BucketName and snsTopicARN](/workshop3/12.png)
</details>

Note: Remember to **save** the file before execute the next command line.

Now, open your terminal again and execute the command `put-delivery-channel`. **A successul command results in nothing**

`aws configservice put-delivery-channel --delivery-channel file://deliveryChannel.json --region YOUR-REGION-CODE`

![CLI](/workshop3/17.1.png)

To view the configuration of channel, execute:

`aws configservice describe-delivery-channels --region YOUR-REGION-CODE`


![CLI](/workshop3/17.2.png)

Again, `describe-delivery-channel-status` will see new thing of configSnapshotDeliveryInfo

`aws configservice describe-delivery-channel-status --region YOUR-REGION-CODE`

![CLI](/workshop3/17.3.png)

If we want to configure Config-Snapshot on-demand instead of waiting for next period of update, use AWS CLI `deliver-config-snapshot`

`aws configservice deliver-config-snapshot --delivery-channel-name default --region YOUR-REGION-CODE`

![CLI](/workshop3/17.4.png)

**Verify again** by CLI, as well as check new object on S3 bucket

`aws configservice describe-delivery-channel-status --region YOUR-REGION-CODE`

![CLI](/workshop3/18.png)



