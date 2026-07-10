---
layout: page
title: DigitalOcean Droplets
---

# DigitalOcean Droplets

## Creating a Droplet

1. Go to the [DigitalOcean Control Panel](https://cloud.digitalocean.com/)
2. Click "Create" → "Droplets"
3. Choose an image (e.g. Ubuntu LTS), plan, and region
4. Add an SSH key for authentication
5. Click "Create Droplet"

## Connecting

```bash
ssh root@your-droplet-ip
```

## Basic Server Setup

```bash
# Update packages
apt update && apt upgrade -y

# Create a non-root user
adduser deploy
usermod -aG sudo deploy

# Set up a firewall
ufw allow OpenSSH
ufw allow 80
ufw allow 443
ufw enable
```

## Deploying an App

```bash
# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
apt install -y nodejs

# Use a process manager
npm install -g pm2
pm2 start app.js
pm2 startup
pm2 save
```

## Troubleshooting

- **Can't connect via SSH**: Check the droplet's firewall/security group and that port 22 is open
- **App not reachable**: Confirm the firewall allows the app's port and a reverse proxy (nginx) is configured
- **Out of memory**: Consider a swap file or resizing the droplet
