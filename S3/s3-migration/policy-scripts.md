# Source Bucket Policy

```json
{
 "Version": "2012-10-17",
 "Statement": [
  {
   "Effect": "Allow",
   "Principal": {
    "AWS": [
     "arn:aws:iam::DIST_ACCOUNT_ID:role/datasync-role",
     "arn:aws:iam::DIST_ACCOUNT_ID:user/destination_account_logged_in_user"
    ]
   },
   "Action": [
    "s3:GetBucketLocation",
    "s3:ListBucket",
    "s3:ListBucketMultipartUploads"
   ],
   "Resource": "arn:aws:s3:::source_bucket"
  },
  {
   "Effect": "Allow",
   "Principal": {
    "AWS": [
     "arn:aws:iam::DIST_ACCOUNT_ID:role/datasync-role",
     "arn:aws:iam::DIST_ACCOUNT_ID:user/destination_account_logged_in_user"
    ]
   },
   "Action": [
    "s3:AbortMultipartUpload",
    "s3:DeleteObject",
    "s3:GetObject",
    "s3:ListMultipartUploadParts",
    "s3:PutObjectTagging",
    "s3:GetObjectTagging",
    "s3:PutObject"
   ],
   "Resource": "arn:aws:s3:::source_bucket/*"
  }
 ]
}
```

# Destination Account Role Policy

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListBucketMultipartUploads"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::source_bucket"
        },
        {
            "Action": [
                "s3:AbortMultipartUpload",
                "s3:DeleteObject",
                "s3:GetObject",
                "s3:ListMultipartUploadParts",
                "s3:PutObject",
                "s3:GetObjectTagging",
                "s3:ListBucket",
                "s3:PutObjectTagging"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::source_bucket/*"
        }
    ]
}
```

# Destination Bucket Policy

```json
{
 "Version": "2008-10-17",
 "Statement": [
  {
   "Sid": "DataSyncCreateS3LocationAndTaskAccess",
   "Effect": "Allow",
   "Principal": {
    "AWS": [
     "arn:aws:iam::DIST_ACCOUNT_ID:role/datasync-role",
     "arn:aws:iam::DIST_ACCOUNT_ID:user/destination_account_logged_in_user"
    ]
   },
   "Action": [
    "s3:GetBucketLocation",
    "s3:ListBucket",
    "s3:ListBucketMultipartUploads",
    "s3:AbortMultipartUpload",
    "s3:DeleteObject",
    "s3:GetObject",
    "s3:ListMultipartUploadParts",
    "s3:PutObject",
    "s3:GetObjectTagging",
    "s3:PutObjectTagging"
   ],
   "Resource": [
    "arn:aws:s3:::destination_bucket",
    "arn:aws:s3:::destination_bucket/*"
   ]
  }
 ]
}
```

# Creating DataSync Location

To create a DataSync location, you can use the AWS CLI command as follows:

```bash
aws datasync create-location-s3 --s3-bucket-arn arn:aws:s3:::admin-bucket-source --s3-storage-class STANDARD --s3-config BucketAccessRoleArn="arn:aws:iam::065865586960:role/datasync-role" --region ap-south-1
```

Replace `"arn:aws:s3:::admin-bucket-source"` with the appropriate ARN for your source bucket and `"arn:aws:iam::065865586960:role/datasync-role"` with the ARN of the IAM role you want to use for DataSync.
```

Make sure to update the ARNs and other parameters as needed to match your specific AWS environment.
```
