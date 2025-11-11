# How to Verify Failed Test Run in GitHub Actions

## 📍 Step-by-Step Guide

### Step 1: Navigate to Actions Page
1. Go to your repository: https://github.com/britbiddle/faleproxy
2. Click on the **"Actions"** tab (top navigation bar)
   - Direct URL: https://github.com/britbiddle/faleproxy/actions

### Step 2: Find Your Workflow Run
1. You should see a list of workflow runs
2. Look for the most recent run (should be at the top)
3. The run should be triggered by your commit: "Add: CI/CD assignment changes - intentional test failure"
4. You'll see either:
   - **🟡 Yellow dot** = Workflow running/in progress
   - **🔴 Red X** = Workflow failed (what we want!)
   - **🟢 Green checkmark** = Workflow passed (not what we want - tests shouldn't pass)

### Step 3: Click on the Workflow Run
1. Click on the workflow run name/description
2. You'll see the workflow details page

### Step 4: Verify Test Job Failed
1. You'll see two jobs: **"test"** and **"deploy"**
2. Look at the **"test"** job:
   - **🔴 Red X** = Tests failed ✅ (This is what we want!)
   - **🟢 Green checkmark** = Tests passed ❌ (This means the bug didn't work)

### Step 5: Check Test Job Details
1. Click on the **"test"** job
2. You'll see it runs on two Node.js versions: **18.x** and **20.x**
3. Both should show **🔴 Red X** (failed)
4. Click on one of them (e.g., "test (18.x)")

### Step 6: Find the Failed Test
1. Scroll down to see the test output
2. Look for sections like:
   - **"Run tests"** - This is where the failure will be
   - Look for red error messages
3. You should see output like:
   ```
   FAIL tests/unit.test.js
     ✕ should handle case-insensitive replacements
   
   Expected: "FALE University, Fale College, and fale medical school"
   Received: "FALE University, Fale College, and yale medical school"
   ```
   (The lowercase "yale" wasn't replaced because of our intentional bug)

### Step 7: Verify What You See

**✅ CORRECT (What you want to see):**
- Red X (❌) next to the test job
- Test output showing failures
- Error messages about case-insensitive replacement
- Both Node.js versions (18.x and 20.x) show failures

**❌ WRONG (If you see this):**
- Green checkmark (✅) - Tests passed
- No failures shown
- This means the intentional bug didn't work as expected

### Step 8: Get the Commit Link
1. Go back to the workflow run page
2. Click on the commit SHA (the short hash, like `811f65f`)
3. Or click on the commit message
4. Copy the full URL from your browser
5. Format: `https://github.com/britbiddle/faleproxy/commits/811f65f`

## 📸 What to Look For

### On the Actions List Page:
```
Actions Tab
├── Faleproxy CI
    ├── 🔴 Add: CI/CD assignment changes... (commit 811f65f)
    ├── 🟢 Previous commit...
    └── ...
```

### On the Workflow Run Page:
```
Faleproxy CI
├── test (18.x) 🔴 ❌ Failed
├── test (20.x) 🔴 ❌ Failed
└── deploy (skipped) ⚪ (because tests failed)
```

### In the Test Output:
```
FAIL tests/unit.test.js
  ✕ should handle case-insensitive replacements

  Expected: "fale medical school"
  Received: "yale medical school"
```

## 🔍 Troubleshooting

### If you don't see any workflow runs:
- Make sure you've **left the fork network** (Settings → Danger Zone)
- Make sure **GitHub Actions are enabled** (Actions tab should show "Enable workflows" if disabled)
- Check that you pushed to the `main` branch

### If tests are passing (green checkmark):
- The intentional bug might not be working
- Check the test output to see what's happening
- You may need to make a different change to break the tests

### If you see "Workflows are disabled on forks":
- You haven't left the fork network yet
- Go to Settings → Danger Zone → Leave fork network
- Then refresh the Actions page

## ✅ Success Indicators

You'll know it's working when you see:
1. ✅ Red X (❌) next to the test job
2. ✅ Failed test output showing case-insensitive replacement failure
3. ✅ Both Node.js versions (18.x and 20.x) failed
4. ✅ Deploy job is skipped (because tests failed)
5. ✅ You can click through to see the commit with the failed run

## 📝 For Submission

When submitting to Canvas, you need:
1. **GitHub commit link** that shows the failed test run:
   - Format: `https://github.com/britbiddle/faleproxy/commits/811f65f`
   - Or: Click the commit SHA in the Actions page
   - **Must show**: The failed workflow run visible on that commit page

2. **Production Vercel URL**:
   - Get from: https://vercel.com/dashboard
   - Should be accessible and working

---

**Quick Check**: If you see red X marks (❌) on the test job, you're good! ✅

