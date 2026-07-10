---
layout: page
title: OAuth 2.0 Setup Guide
---

# OAuth 2.0 Setup

## General OAuth Flow

1. User clicks "Login with [Provider]"
2. Redirect to provider's authorization page
3. User grants permission
4. Provider redirects back with authorization code
5. Exchange code for access token
6. Use access token to get user info

## Getting API Credentials

### Facebook
- Go to [Facebook Developers](https://developers.facebook.com/)
- Create app
- Get App ID and App Secret

### Twitter/X
- Go to [Twitter Developer Portal](https://developer.twitter.com/)
- Create project and app
- Generate API keys

### GitHub
- Go to [GitHub Settings](https://github.com/settings/developers)
- Create OAuth App
- Get Client ID and Client Secret

## Common Implementation Pattern

```javascript
const loginHandler = () => {
  const authURL = `${PROVIDER_URL}?client_id=${CLIENT_ID}&redirect_uri=${REDIRECT_URI}`;
  window.location.href = authURL;
};
```

## Security Best Practices

- Never expose Client Secret in frontend
- Always use HTTPS
- Validate redirect URIs
- Store tokens securely
