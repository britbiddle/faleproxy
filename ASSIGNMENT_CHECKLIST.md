# CI/CD Assignment Checklist - Perfect Score Guide

## 📋 Assignment Requirements (15 points)

### ✅ 1. Fork the Repository
- [x] **DONE**: Repository forked to https://github.com/britbiddle/faleproxy
- [x] Forked from: https://github.com/ChristopherThorpe/faleproxy
- [x] Repository is personal (not cs1060 org)

### ⚠️ 2. Leave the Fork Network (MUST DO MANUALLY)
- [ ] **ACTION REQUIRED**: Go to https://github.com/britbiddle/faleproxy/settings
- [ ] Scroll to **"Danger Zone"** at the bottom
- [ ] Click **"Detach from parent repository"** or **"Leave fork network"**
- [ ] Confirm the action
- [ ] **VERIFY**: Repository should no longer show "forked from" badge

**Why this matters**: Workflows are disabled on forks for security. You must leave the fork network to enable Actions.

### ⚠️ 3. Turn on GitHub Workflows (MUST DO MANUALLY)
- [ ] **ACTION REQUIRED**: Go to https://github.com/britbiddle/faleproxy/actions
- [ ] If you see "Workflows are disabled on forks", click **"Enable workflows"**
- [ ] **VERIFY**: You should see the workflow file listed (`.github/workflows/ci.yml`)
- [ ] After leaving fork network, workflows should auto-enable

**Expected URL**: https://github.com/britbiddle/faleproxy/actions

### ✅ 4. Compare Workflow to Reading
- [x] **DONE**: Workflow file reviewed and matches pattern
- [x] Workflow file: `.github/workflows/ci.yml`
- [x] Reading reference: https://ncodedsolutions.com/en/articles/automate-your-deployments-using-ci-cd-pipeline-with-vercel-and-git-hub-actions
- [x] **VERIFICATION**: Created `WORKFLOW_REVIEW.md` with detailed comparison

**Workflow matches reading pattern**:
- ✅ Tests on multiple Node.js versions (18.x, 20.x)
- ✅ Uses Vercel CLI for deployment
- ✅ Three-step deployment: pull, build, deploy
- ✅ Uses `VERCEL_TOKEN` secret

### ⚠️ 5. Connect to Vercel (MUST DO MANUALLY)
- [ ] **ACTION REQUIRED**: Sign up at https://vercel.com (if needed)
- [ ] **ACTION REQUIRED**: Import your repository:
  - Click "Add New" → "Project"
  - Import `britbiddle/faleproxy`
  - Framework: "Other" or "Node.js"
  - Root Directory: `./` (default)
  - Build Command: (leave empty or `npm start`)
  - Output Directory: (leave empty)
  - Install Command: `npm install`
  - Click "Deploy"
- [ ] **ACTION REQUIRED**: Get Vercel token:
  - Go to: https://vercel.com/account/tokens
  - Click "Create Token"
  - Name: "GitHub Actions Deploy"
  - Copy the token (you won't see it again!)
- [ ] **ACTION REQUIRED**: Add token to GitHub:
  - Go to: https://github.com/britbiddle/faleproxy/settings/secrets/actions
  - Click "New repository secret"
  - Name: `VERCEL_TOKEN` (exactly this)
  - Value: Paste your Vercel token
  - Click "Add secret"

**VERIFY**: 
- Vercel project exists: https://vercel.com/dashboard
- `VERCEL_TOKEN` secret exists in GitHub

### ✅ 6. Make a Minor Change
- [x] **DONE**: Updated README.md with CI/CD assignment note
- [x] **DONE**: Added intentional bug to app.js (removes lowercase 'yale' replacement)
- [x] **DONE**: Committed with descriptive messages
- [x] **DONE**: Pushed to main branch

**Commits made**:
1. `9dbc076` - "Add: CI/CD assignment note to README"
2. `811f65f` - "Add: CI/CD assignment changes - intentional test failure"

**Reference**: Similar to https://github.com/ChristopherThorpe/faleproxy/compare/main...cat1060:faleproxy:main

### ⚠️ 7. Confirm Failed Test Run (MUST VERIFY)
- [ ] **ACTION REQUIRED**: Go to https://github.com/britbiddle/faleproxy/actions
- [ ] Find the workflow run triggered by your push
- [ ] **VERIFY**: Tests should show ❌ FAILED (red X)
- [ ] Click on the failed run to see details
- [ ] **VERIFY**: You should see test failures related to case-insensitive replacement
- [ ] **COPY THE COMMIT LINK**: 
  - Go to: https://github.com/britbiddle/faleproxy/commits/811f65f
  - Or click on the commit SHA in the Actions page
  - Copy the full URL

**Expected failure**: 
- Test: "should handle case-insensitive replacements"
- Reason: Code only replaces uppercase 'Yale', not lowercase 'yale'

### ⚠️ 8. Confirm Preview Deployment in Vercel (MUST VERIFY)
- [ ] **ACTION REQUIRED**: Go to https://vercel.com/dashboard
- [ ] Find your `faleproxy` project
- [ ] **VERIFY**: You should see deployments (preview and/or production)
- [ ] Click on a deployment to see the URL
- [ ] **COPY THE PRODUCTION URL**: 
  - Should be something like: `https://faleproxy-xxx.vercel.app` or `https://faleproxy.vercel.app`
  - Or check your project settings for the production domain

**Note**: Even if tests fail, Vercel may create preview deployments. Check your dashboard.

### ✅ 9. Submit to Canvas
- [ ] **ACTION REQUIRED**: Submit in Canvas:
  - **GitHub commit link**: https://github.com/britbiddle/faleproxy/commits/811f65f
  - **Production Vercel URL**: (get from Vercel dashboard)
  - Make sure both links work and show the required information

## 🔍 Verification Checklist

Before submitting, verify:

- [ ] Repository is **NOT** a fork (no "forked from" badge)
- [ ] GitHub Actions are **enabled** (workflow file visible)
- [ ] Workflow run shows **failed tests** (red X marks)
- [ ] Vercel project is **connected** to GitHub repo
- [ ] `VERCEL_TOKEN` secret is **added** to GitHub
- [ ] Vercel shows **deployments** (preview or production)
- [ ] Commit link shows **failed test run** in Actions
- [ ] Production Vercel URL is **accessible**

## 📝 What You Need to Submit

1. **GitHub commit link with failed test run**:
   - Format: `https://github.com/britbiddle/faleproxy/commits/811f65f`
   - Or: Click the commit SHA in the Actions page
   - **MUST SHOW**: Failed workflow run

2. **Production Vercel URL**:
   - Get from: https://vercel.com/dashboard
   - Should be: `https://faleproxy-xxx.vercel.app` or similar
   - **MUST BE**: Accessible and working

## 🚨 Critical Issues to Fix

If tests **pass** instead of **fail**:
- The intentional bug might not be working
- Check the test output to see what's happening
- May need to make a different change to break tests

If Vercel deployments **don't appear**:
- Check that Vercel project is connected to GitHub
- Verify `VERCEL_TOKEN` secret is set correctly
- Check Vercel dashboard for any error messages

If GitHub Actions **don't run**:
- Make sure you've left the fork network
- Verify workflows are enabled
- Check Actions page for any error messages

## ✅ Final Steps

1. Complete all manual actions (✅ items 2, 3, 5, 7, 8)
2. Verify everything matches the checklist
3. Test both links you'll submit
4. Submit to Canvas with:
   - GitHub commit link (with failed test run visible)
   - Production Vercel URL

---

**Good luck! You've got this! 🎯**

