# Portfolio Deployment Guide for GitHub Pages

This guide will help you deploy your React portfolio to GitHub Pages at: **https://shar-rox.github.io/portfolio/**

## 📋 Prerequisites

- Node.js (v18 or higher) installed on your computer
- Git installed
- GitHub account (you already have the repo at https://github.com/shar-rox/portfolio)

---

## 🚀 Step-by-Step Deployment Instructions

### Step 1: Clone Your Repository (if not already)

```bash
git clone https://github.com/shar-rox/portfolio.git
cd portfolio
```

### Step 2: Copy All Project Files

Copy all the files from this deployment package into your cloned repository:

- `package.json`
- `vite.config.js`
- `tailwind.config.js`
- `postcss.config.js`
- `index.html`
- `.gitignore`
- `src/` folder (with all files inside)

**Your project structure should look like this:**

```
portfolio/
├── src/
│   ├── Portfolio.jsx
│   ├── main.jsx
│   └── index.css
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
└── .gitignore
```

### Step 3: Install Dependencies

Open your terminal in the project folder and run:

```bash
npm install
```

This will install all required packages (React, Vite, Framer Motion, Tailwind CSS, etc.)

### Step 4: Test Locally (Optional but Recommended)

Before deploying, test your site locally:

```bash
npm run dev
```

Open your browser and go to `http://localhost:5173` to see your portfolio.

Press `Ctrl+C` in the terminal to stop the dev server when done.

### Step 5: Configure GitHub Pages

1. Go to your GitHub repository: https://github.com/shar-rox/portfolio
2. Click on **Settings** (top menu)
3. Click on **Pages** (left sidebar)
4. Under "Build and deployment":
   - Source: Select **"GitHub Actions"**
   
Leave this page open, we'll come back to it.

### Step 6: Create GitHub Actions Workflow

Create a new folder and file in your project:

```
.github/workflows/deploy.yml
```

Create the folders if they don't exist:

```bash
mkdir -p .github/workflows
```

Then create the file `.github/workflows/deploy.yml` with this content:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build
        run: npm run build
        
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Step 7: Push to GitHub

Now commit and push all files:

```bash
# Add all files
git add .

# Commit with a message
git commit -m "Initial portfolio deployment setup"

# Push to GitHub (make sure you're on the main branch)
git push origin main
```

**Note:** If your default branch is `master` instead of `main`, use:
```bash
git push origin master
```

And update the `deploy.yml` file to use `master` instead of `main` in the `branches:` section.

### Step 8: Wait for Deployment

1. Go to your repository on GitHub
2. Click on **Actions** tab
3. You should see a workflow running (yellow dot 🟡)
4. Wait for it to complete (green checkmark ✅)

This usually takes 1-3 minutes.

### Step 9: View Your Live Site! 🎉

Once the workflow is complete, your site will be live at:

**https://shar-rox.github.io/portfolio/**

You can also find this URL in:
- Settings → Pages → "Your site is live at..."
- Or in the Actions tab after deployment completes

---

## 🔄 Making Updates

Whenever you want to update your portfolio:

1. Make your changes in the code
2. Run `git add .`
3. Run `git commit -m "Description of changes"`
4. Run `git push origin main`

GitHub Actions will automatically rebuild and redeploy your site!

---

## ⚠️ Troubleshooting

### Issue: Site shows 404 or blank page

**Solution:** Make sure in your GitHub repository settings:
- Settings → Pages → Source is set to "GitHub Actions"

### Issue: Styles not loading

**Solution:** Check that `vite.config.js` has the correct `base` path:
```js
base: '/portfolio/',  // This should match your repo name
```

### Issue: Build fails in GitHub Actions

**Solution:** Check the Actions tab for error details. Common fixes:
- Make sure all dependencies are in `package.json`
- Verify Node version (should be 18+)
- Check for typos in file names

### Issue: Assets (images) not loading

**Solution:** Place images in the `public` folder and reference them as `/image.png`

---

## 📝 Quick Reference Commands

```bash
npm install          # Install dependencies
npm run dev          # Run development server
npm run build        # Build for production
npm run preview      # Preview production build
git add .            # Stage all changes
git commit -m "msg"  # Commit changes
git push origin main # Push to GitHub
```

---

## 🎨 Customization Tips

- Edit `src/Portfolio.jsx` to change content
- Modify colors in the component's gradient classes
- Update projects, skills, and certificates arrays
- Add new sections by following the existing pattern

---

## 📞 Need Help?

If you encounter any issues:
1. Check the GitHub Actions logs for error messages
2. Verify all files are correctly placed
3. Ensure all dependencies are installed
4. Make sure you're using Node.js v18 or higher

---

## ✅ Checklist

- [ ] All files copied to repository
- [ ] `npm install` completed successfully
- [ ] Tested locally with `npm run dev`
- [ ] `.github/workflows/deploy.yml` created
- [ ] GitHub Pages source set to "GitHub Actions"
- [ ] Code pushed to GitHub
- [ ] GitHub Actions workflow completed
- [ ] Site is live at https://shar-rox.github.io/portfolio/

---

**That's it! Your portfolio is now live on GitHub Pages! 🚀**
