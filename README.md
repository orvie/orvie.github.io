# 📚 Orvie's Knowledge Base

Welcome to my personal knowledge base! This is where I document project notes, configuration tips, and learning resources. Navigate using the sections below.

---

## 📑 Table of Contents

### 🚀 [Web Deployment](#-web-deployment)
- AWS S3 & CloudFront
- React App Deployment
- Configuration & Troubleshooting

### 🔗 [Social Networks](#-social-networks)
- Social Media Integration
- OAuth & Authentication
- Platform Configuration

### 🤖 [AI & Self-Study](#-ai--self-study)
- Machine Learning Basics
- LLM Resources
- Deep Learning
- Tools & Frameworks

### 💡 [Quick Reference](#-quick-reference)
- Common Commands
- Useful Links
- Tools & Resources

---

## 🚀 Web Deployment

### AWS S3 & CloudFront

#### Overview
Setting up a React application with AWS S3 for static hosting and CloudFront for CDN distribution.

**Resources:**
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)

#### Key Steps
1. **Create S3 Bucket** - Static website hosting
2. **Configure CloudFront** - CDN distribution
3. **Set IAM Policies** - Access permissions
4. **Cache Configuration** - Optimization

**Related Files:**
- [AWS Configuration Guide](./docs/web-deployment/aws-s3-cloudfront-setup.md)
- [React Build & Deploy](./docs/web-deployment/react-deployment.md)
- [Troubleshooting](./docs/web-deployment/troubleshooting.md)

---

## 🔗 Social Networks

### Social Media Integration

Configuration guides for integrating social networks into your applications.

**Supported Platforms:**
- Facebook
- Twitter / X
- Instagram
- LinkedIn
- GitHub

**Topics:**
- OAuth 2.0 Setup
- API Keys & Credentials
- Authentication Flows
- Rate Limiting & Best Practices

**Related Files:**
- [OAuth Configuration](./docs/social-networks/oauth-setup.md)
- [Platform-Specific Guides](./docs/social-networks/)
- [Security Best Practices](./docs/social-networks/security.md)

---

## 🤖 AI & Self-Study

### Learning Tracks

#### 1️⃣ **Machine Learning Fundamentals**
- Supervised Learning
- Unsupervised Learning
- Neural Networks
- Deep Learning Basics

#### 2️⃣ **Large Language Models (LLMs)**
- Transformer Architecture
- Prompt Engineering
- Fine-tuning Approaches
- Retrieval Augmented Generation (RAG)

#### 3️⃣ **Deep Learning**
- CNN (Convolutional Neural Networks)
- RNN & LSTM
- Attention Mechanisms
- Vision Transformers

#### 4️⃣ **Tools & Frameworks**
- TensorFlow & Keras
- PyTorch
- Hugging Face Transformers
- OpenAI API & LangChain

**Related Files:**
- [AI Learning Roadmap](./docs/ai-study/learning-roadmap.md)
- [ML Algorithms](./docs/ai-study/ml-algorithms.md)
- [LLM Guide](./docs/ai-study/llm-guide.md)
- [Frameworks & Tools](./docs/ai-study/frameworks.md)
- [Resources & Papers](./docs/ai-study/resources.md)

---

## 💡 Quick Reference

### Essential Commands

#### AWS CLI
```bash
# Upload to S3
aws s3 cp build/ s3://your-bucket-name --recursive

# Invalidate CloudFront cache
aws cloudfront create-invalidation --distribution-id YOUR_ID --paths "/*"
```

#### React Development
```bash
# Build for production
npm run build

# Development server
npm start
```

#### Git Workflow
```bash
git add .
git commit -m "Update knowledge base"
git push origin main
```

### Useful Links
- [AWS Console](https://console.aws.amazon.com/)
- [React Documentation](https://react.dev/)
- [GitHub Pages Docs](https://pages.github.com/)
- [Hugging Face Hub](https://huggingface.co/)

---

## 📖 How to Use This Knowledge Base

1. **Navigate by Section** - Use the links above to jump to topics
2. **Check Documentation** - Each section has detailed markdown files
3. **Search** - Use GitHub's search feature (press `/` on the page)
4. **Contribute** - Update notes as you learn new things!

---

## 📝 Notes

- Last Updated: July 10, 2026
- Status: 🔄 Work in Progress
- Contributing: Feel free to add notes and improve documentation!

---

## 🔗 Connect

- [GitHub Profile](https://github.com/orvie)
- [Email](mailto:your-email@example.com)
- [Twitter](https://twitter.com/your-handle)

---

**Made with ❤️ for future reference**
