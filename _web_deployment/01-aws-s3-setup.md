---
layout: page
title: AWS S3 & CloudFront Setup
---

# AWS S3 & CloudFront Setup

## Step 1: Create S3 Bucket

1. Go to [AWS S3 Console](https://s3.console.aws.amazon.com/)
2. Click "Create bucket"
3. Enter bucket name (must be globally unique)
4. Uncheck "Block public access" for website hosting
5. Enable "Static website hosting" in bucket properties

## Step 2: Configure CloudFront

1. Go to CloudFront console
2. Create distribution
3. Set S3 bucket as origin
4. Configure cache behaviors
5. Set default root object to `index.html`

## Step 3: Upload Files

```bash
aws s3 cp build/ s3://your-bucket-name --recursive
```

## Step 4: Test

Visit your CloudFront domain URL to verify deployment.
