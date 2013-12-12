travis-s3-test
==============

S3 policy

```
{
  "Statement": [
    {
      "Action": [
        "s3:ListBucket"
      ],
      "Effect": "Allow",
      "Resource": [
        "arn:aws:s3:::your-bucket"
      ]
    },
    {
      "Action": [
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
      "Effect": "Allow",
      "Resource": [
        "arn:aws:s3:::your-bucket/*"
      ]
    }
  ]
}

```
