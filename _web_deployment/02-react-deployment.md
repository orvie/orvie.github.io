---
layout: page
title: React App Deployment
---

# Deploying React Apps

## Build Your React App

```bash
npm run build
```

This creates an optimized `build/` folder.

## Upload to S3

```bash
aws s3 sync build/ s3://your-bucket-name --delete
```

## Invalidate CloudFront Cache

```bash
aws cloudfront create-invalidation --distribution-id YOUR_ID --paths "/*"
```

## Environment Variables

Create a `.env` file:

```
REACT_APP_API_URL=https://api.example.com
REACT_APP_ENV=production
```

## Troubleshooting

- **Blank page**: Check browser console for errors
- **404 errors**: Ensure `index.html` is CloudFront default root object
- **Old content showing**: CloudFront cache might need invalidation
