---
layout: page
title: CloudFront CDN
---

# CloudFront CDN

## Creating a Distribution

1. Go to the [CloudFront Console](https://console.aws.amazon.com/cloudfront/)
2. Click "Create Distribution"
3. Set the origin (e.g. an S3 bucket or load balancer)
4. Configure the default cache behavior
5. Set the default root object (e.g. `index.html`)

## Cache Invalidation

```bash
aws cloudfront create-invalidation --distribution-id YOUR_DISTRIBUTION_ID --paths "/*"
```

## Custom Domain + HTTPS

1. Request or import a certificate in [AWS Certificate Manager](https://console.aws.amazon.com/acm/) (must be in `us-east-1`)
2. Attach the certificate to the distribution
3. Add a CNAME/alias record in DNS pointing to the distribution's domain name

## Common Cache Behaviors

- **Static assets** (`/static/*`): long TTL, cache based on path only
- **API routes** (`/api/*`): TTL 0, forward all headers/cookies/query strings
- **SPA fallback**: custom error response mapping 403/404 to `/index.html` with status 200

## Troubleshooting

- **Changes not showing**: Cache invalidation can take several minutes to propagate
- **403/404 on refresh (SPA)**: Add custom error responses for 403/404 → `/index.html`
- **SSL errors on custom domain**: Certificate must be issued in `us-east-1` regardless of distribution region
