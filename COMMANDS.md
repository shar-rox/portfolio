# 💻 EXACT COMMANDS TO RUN

Copy and paste these commands in order. This is the complete deployment process.

---

## 🔵 Phase 1: Get Your Repository

### Option A: If you haven't cloned yet
```bash
cd ~/Desktop  # or wherever you want the folder
git clone https://github.com/shar-rox/portfolio.git
cd portfolio
```

### Option B: If you already have it cloned
```bash
cd /path/to/your/portfolio  # navigate to your existing folder
```

---

## 🔵 Phase 2: Copy Files

1. **Download this deployment package** to your computer
2. **Copy ALL files** into your `portfolio/` folder
3. **Verify** the structure matches FILE_STRUCTURE.md

**Or use terminal to copy (if files are in Downloads):**
```bash
cp -r ~/Downloads/deployment-package/* .
cp -r ~/Downloads/deployment-package/.github .
cp ~/Downloads/deployment-package/.gitignore .
```

---

## 🔵 Phase 3: Install & Test

### Install dependencies
```bash
npm install
```

**Expected output:** ✅ "added XXX packages"

### Test locally (recommended)
```bash
npm run dev
```

**Expected output:**
```
VITE v5.x.x ready in XXX ms
➜ Local: http://localhost:5173/
```

Open `http://localhost:5173/` in browser - looks good? ✅

Press `Ctrl+C` to stop the server.

---

## 🔵 Phase 4: Configure GitHub Pages

**In your browser:**

1. Go to: `https://github.com/shar-rox/portfolio/settings/pages`
2. Under "Build and deployment"
3. Click **Source** dropdown
4. Select **"GitHub Actions"**
5. The page will reload - that's normal ✅

---

## 🔵 Phase 5: Deploy!

### Check your branch name first
```bash
git branch
```

Look for the `*` - is it next to `main` or `master`?

### If it's `main` (most common):
```bash
git add .
git commit -m "Deploy React portfolio to GitHub Pages"
git push origin main
```

### If it's `master`:
First, update `.github/workflows/deploy.yml` line 4:
- Change `branches: [ main ]` to `branches: [ master ]`

Then:
```bash
git add .
git commit -m "Deploy React portfolio to GitHub Pages"
git push origin master
```

**Expected output:** ✅ "Branch 'main' set up to track..."

---

## 🔵 Phase 6: Watch Deployment

**In your browser:**

1. Go to: `https://github.com/shar-rox/portfolio/actions`
2. You should see a workflow running (yellow dot 🟡)
3. Click on it to watch progress
4. Wait for green checkmark ✅ (2-3 minutes)

**Timeline:**
- 0:00 - Workflow starts
- 0:30 - Dependencies installing
- 1:00 - Building project
- 1:30 - Uploading to Pages
- 2:00 - Deploying
- 2:30 - ✅ Complete!

---

## 🔵 Phase 7: View Your Site!

**Open in browser:**
```
https://shar-rox.github.io/portfolio/
```

🎉 **IT'S LIVE!** 🎉

---

## 🔄 Making Changes Later

Whenever you want to update your portfolio:

```bash
# 1. Make your edits in src/Portfolio.jsx

# 2. Test locally (optional)
npm run dev

# 3. Commit and push
git add .
git commit -m "Updated project section"
git push origin main

# 4. Wait 2-3 minutes for auto-deployment
# 5. Refresh https://shar-rox.github.io/portfolio/
```

That's it! Automatic redeployment! 🚀

---

## ⚠️ If Something Goes Wrong

### Error: "npm: command not found"
**Install Node.js:**
```bash
# macOS
brew install node

# Windows - download from nodejs.org

# Linux (Ubuntu/Debian)
sudo apt update
sudo apt install nodejs npm
```

### Error: "Permission denied"
```bash
sudo chown -R $USER ~/.npm
```

### Error: "GitHub Actions failed"
1. Go to Actions tab
2. Click the failed workflow
3. Look for red ❌ error message
4. Common fixes:
   - Check branch name (main vs master)
   - Verify package.json is valid JSON
   - Ensure all files are committed

### Error: "Site shows 404"
**Check these:**
1. GitHub Pages source = "GitHub Actions" ✅
2. `vite.config.js` has `base: '/portfolio/'` ✅
3. Wait 5 minutes (sometimes takes time)
4. Clear browser cache (Ctrl+Shift+R)

---

## 🎯 Quick Test Commands

**Check if Node.js is installed:**
```bash
node --version  # Should show v18+ or v20+
npm --version   # Should show 9+ or 10+
```

**Check if Git is installed:**
```bash
git --version  # Should show 2.x.x
```

**Check current directory:**
```bash
pwd  # Shows your current location
ls   # Lists files in current directory
```

**Check Git status:**
```bash
git status  # Shows what's changed
git log --oneline -5  # Shows last 5 commits
```

---

## ✅ Success Verification

After deployment, verify these:

**Portfolio loads:**
- [ ] https://shar-rox.github.io/portfolio/ works
- [ ] No console errors (F12 → Console tab)

**Content displays:**
- [ ] Hero section with typing animation
- [ ] About section
- [ ] Projects section with all 4 projects
- [ ] Skills section
- [ ] Certificates section
- [ ] Contact section

**Functionality works:**
- [ ] Smooth scrolling
- [ ] Hover animations
- [ ] All links work
- [ ] Responsive on mobile

**Performance:**
- [ ] Page loads in <3 seconds
- [ ] Animations are smooth
- [ ] No missing images/icons

---

**Need the full guide?** See README.md  
**Want quick start?** See QUICK_START.md  
**File structure help?** See FILE_STRUCTURE.md  

---

## 🏁 Ready? Let's Go!

Start with Phase 1 and work through each phase in order.

**Time estimate:** 5-10 minutes total

**You've got this! 🚀**
