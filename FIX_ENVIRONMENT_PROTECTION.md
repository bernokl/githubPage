# How to Fix "Branch Not Allowed" Error

## The Problem

GitHub Pages environments have **protection rules** that restrict which branches can deploy. Your `hugo_conversion` branch is being blocked.

## Solution: Configure Environment Settings

You need to allow your branch in the GitHub Pages environment settings:

### Step-by-Step Instructions

1. **Go to your repository on GitHub**
   - Navigate to: `https://github.com/bernokl/githubPage`

2. **Open Settings**
   - Click on **Settings** tab (top menu)

3. **Go to Environments**
   - In the left sidebar, click **Environments**
   - Click on **github-pages** environment

4. **Configure Deployment Branches**
   - Scroll down to **Deployment branches** section
   - You'll see options:
     - **Selected branches** (current - only allows specific branches)
     - **All branches** (allows any branch)
     - **Protected branches only** (only protected branches)

5. **Select "All branches"**
   - Choose **All branches** option
   - This will allow `hugo_conversion` and any other branch to deploy

6. **Save**
   - Click **Save protection rules** or the changes will auto-save

## Alternative: Add Specific Branch

If you prefer to keep restrictions but allow `hugo_conversion`:

1. In **Deployment branches**, select **Selected branches**
2. Click **Add branch**
3. Type: `hugo_conversion`
4. Click **Save**

## After Making Changes

1. **Re-run the workflow**
   - Go to **Actions** tab
   - Find your failed workflow run
   - Click **Re-run all jobs**

2. **Or trigger manually**
   - Go to **Actions** → **Deploy Hugo Site to GitHub Pages**
   - Click **Run workflow**
   - Select branch: `hugo_conversion`
   - Click **Run workflow**

## Visual Guide

```
Repository → Settings → Environments → github-pages
                                           ↓
                                    Deployment branches
                                           ↓
                              [ ] Selected branches
                              [✓] All branches  ← Select this
                              [ ] Protected branches only
```

## If You Don't See "Environments" Option

If you don't see **Environments** in Settings:
- You might need repository admin access
- Or the environment might not exist yet (it's created automatically when first used)
- Try running the workflow once, then check Settings again

## Quick Fix Summary

**Problem:** Branch protection blocking deployment  
**Solution:** Settings → Environments → github-pages → Deployment branches → All branches  
**Time:** 30 seconds  
**Result:** Any branch can now deploy ✅
