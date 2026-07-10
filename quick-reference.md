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
