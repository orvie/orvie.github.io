---
layout: page
title: Quick Reference
permalink: /quick-reference/
---

# 💡 Quick Reference

Common commands, useful links, and frequently used resources.

## AWS CLI Commands

```bash
# Upload directory to S3
aws s3 cp ./build s3://your-bucket-name --recursive --acl public-read

# Invalidate CloudFront distribution
aws cloudfront create-invalidation --distribution-id YOUR_DISTRIBUTION_ID --paths "/*"

# List S3 buckets
aws s3 ls

# Sync folder (with delete)
aws s3 sync ./build s3://your-bucket-name --delete
```

## React Commands

```bash
# Create new React app
npx create-react-app my-app

# Install dependencies
npm install

# Start development server
npm start

# Build for production
npm run build

# Run tests
npm test
```

## Initial Git Setup

```bash
# Set your name and email (used in commit metadata)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Check current config
git config --global --list

# Set default branch name for new repos
git config --global init.defaultBranch main

# Generate a new SSH key for GitHub
ssh-keygen -t ed25519 -C "you@example.com"

# If your system doesn't support ed25519, use RSA instead
ssh-keygen -t rsa -b 4096 -C "you@example.com"

# Start the ssh-agent and add your key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key to clipboard to paste into GitHub > Settings > SSH Keys
cat ~/.ssh/id_ed25519.pub

# Test the SSH connection to GitHub
ssh -T git@github.com
```

**`ssh-keygen -t` values:**
- `ed25519` - Recommended default. Modern, fast, small keys, strong security.
- `rsa` - Widely supported legacy option; use with `-b 4096` for adequate strength.
- `ecdsa` - Elliptic curve alternative to RSA; less commonly recommended than ed25519.
- `dsa` - Deprecated, insecure, and disabled by OpenSSH — avoid.

## Multiple Hosts / SSH Keys (Avoiding Conflicts)

When you have more than one account on the same host (e.g. personal + work GitHub) or multiple keys for different hosts, generate a separate key per identity and map each to a distinct SSH alias instead of overwriting `~/.ssh/id_ed25519`.

```bash
# Generate a separate, uniquely named key per account/host
ssh-keygen -t ed25519 -C "personal@example.com" -f ~/.ssh/id_ed25519_personal
ssh-keygen -t ed25519 -C "you@work.com" -f ~/.ssh/id_ed25519_work

# Add both keys to the agent
ssh-add ~/.ssh/id_ed25519_personal
ssh-add ~/.ssh/id_ed25519_work

# List keys currently loaded in the agent
ssh-add -l
```

Create/edit `~/.ssh/config` with a `Host` alias per identity, pointing at the real hostname via `HostName`:

```
# Personal GitHub account
Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_personal
    IdentitiesOnly yes

# Work GitHub account
Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_work
    IdentitiesOnly yes
```

Use the alias instead of `github.com` when cloning or setting a remote:

```bash
git clone git@github-personal:orvie/orvie.github.io.git

# Or update an existing repo's remote to use the alias
git remote set-url origin git@github-work:your-org/some-repo.git

# Verify which key/identity is used for a given alias
ssh -T git@github-personal
```

Set the correct name/email **per repository** (overrides `--global`) so commits attribute to the right identity:

```bash
git config user.name "Work Name"
git config user.email "you@work.com"
```

**Notes:**
- `IdentitiesOnly yes` stops SSH from trying every key in the agent (which can trigger GitHub's "too many authentication failures" error) and forces it to use only the `IdentityFile` specified.
- Without a `Host` alias, SSH has no way to tell two `github.com` identities apart — the alias is what makes per-account routing possible.

## Git Commands

```bash
# Clone repository
git clone https://github.com/orvie/orvie.github.io.git

# Check status
git status

# Add changes
git add .

# Commit changes
git commit -m "Your commit message"

# Push to main branch
git push origin main

# Pull latest changes
git pull origin main

# Create and switch to new branch
git checkout -b feature-branch-name
```

## Python Commands

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows

# Install requirements
pip install -r requirements.txt

# Install package
pip install package-name

# List installed packages
pip list
```

## Useful Links

### AWS & Deployment
- [AWS Console](https://console.aws.amazon.com/)
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [CloudFront Docs](https://docs.aws.amazon.com/cloudfront/)

### Web Development
- [React Documentation](https://react.dev/)
- [MDN Web Docs](https://developer.mozilla.org/)
- [Can I Use](https://caniuse.com/)

### AI & ML
- [Hugging Face Hub](https://huggingface.co/)
- [OpenAI Platform](https://platform.openai.com/)
- [TensorFlow Docs](https://tensorflow.org/)
- [PyTorch Docs](https://pytorch.org/)

### Tools & Resources
- [GitHub](https://github.com/)
- [Stack Overflow](https://stackoverflow.com/)
- [Dev.to](https://dev.to/)

## Online Editors & IDEs

- [VS Code](https://code.visualstudio.com/) - Code editor
- [GitHub Codespaces](https://github.com/features/codespaces) - Cloud IDE
- [Colab](https://colab.research.google.com/) - Jupyter notebooks for ML
- [Replit](https://replit.com/) - Online IDE

## Keyboard Shortcuts

### VS Code
- `Ctrl+K Ctrl+S` - Keyboard shortcuts reference
- `Ctrl+/` - Toggle comment
- `Alt+Shift+Down` - Copy line down
- `Ctrl+D` - Select word
- `Ctrl+Shift+P` - Command palette

### GitHub
- `?` - Open shortcuts menu
- `/` - Open command palette
- `.` - Open in web editor

---

**Tip:** Bookmark this page for quick reference!
