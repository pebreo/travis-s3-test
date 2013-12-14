Purpose
==============
This is just a skeleton repo that demonstrates how to use Travis CI and then transfer a file created during the test run to an Amazon AWS S3 bucket.

S3 policy
=========
This is the Amazon AWS S3 bucket policy that you copy and paste in your bucket configuration. 
To insert this policy you have to click on your bucket then click `Properties button -> Permissions -> Add bucket policy.` 

```
{
    "Version": "2013-12-13",
    "Id": "12345",
    "Statement": [
        {
            "Sid": "1",
            "Action": "s3:ListBucket",
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::bucket-name",
            "Principal": { "AWS": "xxxx-xxxx-xxxx"}
        },
        {
            "Sid": "2",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::bucket-name/*",
            "Principal": {"AWS": "xxxx-xxxx-xxxx"}
        }
    ]
}


```
