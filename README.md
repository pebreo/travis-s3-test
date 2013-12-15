Purpose
==============
This is just a skeleton repo that demonstrates how to use Travis CI and then transfer a file created during the test run to an Amazon AWS S3 bucket.


Travis CI
=========
Travis CI allows you and your team to automatically run tests on your GitHub repo(s). It makes it easy for your team to identify bugs before you deploy. To automate the process, Travis listens to your GitHub repo for any changes then it spins up a linux virtual machine and does a `git pull` on your repository and runs your tests scripts. You setup your tests scripts in the `.travis.yaml` file.  

The three steps to enable Travis CI automated tests on your repo are:

1) Sign up for a free account at travis-ci.org (if you want a private repo you must pay GitHub and Travis)

2) Create and configure a `.travis.yml` at the top of your repo

3) Tell Travis to listen for any changes in your repo so it can automatically run your tests. To do that, you click `Your name (top right) -> Select which repos to turn ON or OFF` 

Amazon Web Services (AWS)
=========
AWS provides web services for cloud computer and cloud storage. One of those services is S3 which provides cloud storage. You sign up for a free account and at the time of writing they give 5GB storage, 20,000 Get Requests, and 2,000 Put Requests which is not bad if you are just doing personal computing stuff.


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
