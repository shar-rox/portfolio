# 🚀 QUICK START - Deploy in 5 Minutes!

## What You Need to Do RIGHT NOW:

### 1️⃣ Download All Files
Download this entire deployment package to your computer.

### 2️⃣ Navigate to Your Repository
```bash
cd /path/to/your/portfolio-folder
```

If you haven't cloned it yet:
```bash
git clone https://github.com/shar-rox/portfolio.git
cd portfolio
```

### 3️⃣ Copy All Files
Copy EVERYTHING from the deployment package into your repository folder:
- ✅ All files in the root
- ✅ The `src/` folder 
- ✅ The `.github/` folder

### 4️⃣ Install & Test
```bash
npm install
npm run dev
```

Visit `http://localhost:5173` - Does it look good? ✅

### 5️⃣ Enable GitHub Pages
1. Go to: https://github.com/shar-rox/portfolio/settings/pages
2. Under "Build and deployment"
3. Set **Source** to: **GitHub Actions**

### 6️⃣ Push to GitHub
```bash
git add .
git commit -m "Deploy React portfolio to GitHub Pages"
git push origin main
```

*Note: If your branch is `master` not `main`, use `git push origin master` and update line 4 in `.github/workflows/deploy.yml`*

### 7️⃣ Wait & Watch
1. Go to: https://github.com/shar-rox/portfolio/actions
2. Watch the deployment (2-3 minutes)
3. ✅ When complete, visit: **https://shar-rox.github.io/portfolio/**

---

## 🎉 DONE! Your site is LIVE!

Any time you push changes to GitHub, it will automatically redeploy!

---

## ⚡ Even Faster: One-Command Deploy

If you're comfortable with terminal, after copying files:

```bash
npm install && git add . && git commit -m "Initial deploy" && git push origin main
```

Then just wait for GitHub Actions to finish!

---

## ❓ Problems?

**Check GitHub Pages settings**: Source = "GitHub Actions" ✅  
**Check branch name**: main vs master  
**Check Actions tab**: https://github.com/shar-rox/portfolio/actions  

See README.md for detailed troubleshooting.
