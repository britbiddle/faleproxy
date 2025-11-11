# CI/CD Assignment Steps

## 📋 Assignment Checklist

Follow these steps to complete your CI/CD assignment:

### Step 1: Leave the Fork Network ✅

1. Go to your repository: https://github.com/britbiddle/faleproxy
2. Click **Settings** (top right of the repository page)
3. Scroll down to **Danger Zone** (at the bottom)
4. Click **"Detach from parent repository"** or **"Leave fork network"**
5. Confirm the action

**Why**: This makes your repository independent and allows you to enable GitHub Actions.

### Step 2: Enable GitHub Actions ✅

1. Go to: https://github.com/britbiddle/faleproxy/actions
2. If you see a message saying "Workflows are disabled on forks", click **"Enable workflows"**
3. If workflows are already enabled, you should see the workflow file listed

**Note**: After leaving the fork network, workflows should automatically be enabled. If not, you'll see a button to enable them.

### Step 3: Review the CI/CD Workflow

The workflow file is located at: `.github/workflows/ci.yml`

**What it does:**
- Runs on pushes to `main`/`master` and pull requests
- Tests on Node.js 18.x and 20.x
- Runs `npm run test:ci` (tests with coverage)
- Deploys to Vercel (production) when tests pass on main/master

**Compare with the reading**: 
- The workflow follows the pattern from: https://ncodedsolutions.com/en/articles/automate-your-deployments-using-ci-cd-pipeline-with-vercel-and-git-hub-actions
- It uses Vercel CLI to build and deploy

### Step 4: Connect to Vercel

1. **Create Vercel Account** (if you don't have one):
   - Go to: https://vercel.com
   - Sign up with your GitHub account

2. **Create a New Project**:
   - Click "Add New" → "Project"
   - Import your repository: `britbiddle/faleproxy`
   - Configure:
     - Framework Preset: "Other" or "Node.js"
     - Root Directory: `./` (default)
     - Build Command: (leave empty or use `npm start`)
     - Output Directory: (leave empty)
     - Install Command: `npm install`
   - Click "Deploy"

3. **Get Vercel Token**:
   - Go to: https://vercel.com/account/tokens
   - Click "Create Token"
   - Name it: "GitHub Actions Deploy"
   - Copy the token (you won't see it again!)

4. **Add Token to GitHub Secrets**:
   - Go to: https://github.com/britbiddle/faleproxy/settings/secrets/actions
   - Click "New repository secret"
   - Name: `VERCEL_TOKEN`
   - Value: Paste your Vercel token
   - Click "Add secret"

### Step 5: Make a Minor Change

Based on the example: https://github.com/ChristopherThorpe/faleproxy/compare/main...cat1060:faleproxy:main

You can make a simple change like:
- Update README.md with your name/credits
- Add a comment to app.js
- Update a version number
- Add a new feature

**Example change** (update README):

```markdown
## About

This project was forked and modified as part of a CI/CD assignment.

## Contributors

- [Your Name]
```

### Step 6: Push Changes and Verify

1. **Make your change locally**:
   ```bash
   cd faleproxy
   # Edit a file (README.md, app.js, etc.)
   git add .
   git commit -m "Add: Minor change for CI/CD assignment"
   git push origin main
   ```

2. **Check GitHub Actions**:
   - Go to: https://github.com/britbiddle/faleproxy/actions
   - You should see a workflow run in progress
   - **Expected**: Tests should FAIL (as per assignment requirement)
   - Click on the workflow run to see details

3. **Check Vercel**:
   - Go to: https://vercel.com/dashboard
   - Find your `faleproxy` project
   - You should see a preview deployment created
   - Click on it to see the deployment

### Step 7: Confirm Requirements Met ✅

- [ ] Repository is no longer a fork (detached)
- [ ] GitHub Actions are enabled
- [ ] Workflow file exists and matches the reading pattern
- [ ] Repository connected to Vercel
- [ ] VERCEL_TOKEN secret added to GitHub
- [ ] Made a minor change and pushed
- [ ] GitHub Actions run shows failed tests (or running)
- [ ] Vercel shows a preview deployment

## 🐛 Troubleshooting

### "Workflows disabled on forks"
- Make sure you've left the fork network (Step 1)
- Refresh the Actions page
- Click "Enable workflows" if the button appears

### "Tests are passing instead of failing"
- The assignment asks to confirm a failed test run
- You might need to intentionally break a test, or
- The example might show a scenario where tests fail
- Check the example comparison link for what change was made

### "Vercel deployment not working"
- Verify VERCEL_TOKEN is set correctly in GitHub secrets
- Check Vercel dashboard for any error messages
- Make sure the Vercel project is connected to your GitHub repo

### "Can't find Actions tab"
- Make sure you've left the fork network
- Check that you're logged into the correct GitHub account
- The Actions tab should appear after leaving fork network

## 📚 Resources

- **CI/CD Reading**: https://ncodedsolutions.com/en/articles/automate-your-deployments-using-ci-cd-pipeline-with-vercel-and-git-hub-actions
- **Example Change**: https://github.com/ChristopherThorpe/faleproxy/compare/main...cat1060:faleproxy:main
- **Your Repository**: https://github.com/britbiddle/faleproxy
- **GitHub Actions**: https://github.com/britbiddle/faleproxy/actions
- **Vercel Dashboard**: https://vercel.com/dashboard

---

**Ready to start?** Begin with Step 1 and work through each step!

