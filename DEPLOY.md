# Deploy to GitHub + Vercel

These are the exact steps to get the dashboard live. Once done, every push to `main` auto-redeploys.

---

## Step 1 — Create the GitHub repo

1. Go to [github.com](https://github.com) → **New repository**
2. Name it: `equity-dashboard`
3. Set to **Public** (required for free Vercel auto-deploy)
4. Do NOT initialize with a README (you already have one)
5. Click **Create repository**

---

## Step 2 — Push this folder to GitHub

Open Terminal, navigate to this folder, then run:

```bash
cd /Users/huddahkamran/Desktop/Knowledge/equity-dashboard

git init
git add .
git commit -m "Initial deploy: Employment Equity Gap Dashboard TBS 2024-25"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/equity-dashboard.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

---

## Step 3 — Deploy on Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New Project**
2. Click **Import Git Repository** → connect your GitHub account if not already
3. Select `equity-dashboard`
4. Framework preset: **Other** (it's a static site)
5. Leave all settings as default
6. Click **Deploy**

Vercel will give you a live URL (e.g., `equity-dashboard-abc123.vercel.app`).  
Add a custom domain if you want (optional).

---

## Step 4 — Set up the pull request review workflow

This mirrors the course requirement: every change to `main` passes one human review first.

1. On GitHub → your repo → **Settings** → **Branches**
2. Under **Branch protection rules** → **Add rule**
3. Branch name pattern: `main`
4. Check: **Require a pull request before merging**
5. Check: **Require approvals** (set to 1)
6. Save

**From now on:** Make changes on a branch → open a Pull Request → review → merge. Merging to `main` auto-deploys.

---

## Step 5 — Confirm the oracle on the live URL

After deploy, open the live URL and check:

- Go to **Explore Gaps** → filter to **Persons with Disabilities**
- Find **Royal Canadian Mounted Police**
- Confirm: **5.5% (N=590 of 10,822) · WFA 12.0% · Gap −709 · ⚑**

If those values match, the live app is correct.

---

## Daily update loop

```bash
# Make a change
git checkout -b fix/description-of-change
# edit files
git add .
git commit -m "Description of what changed"
git push origin fix/description-of-change
# Then open a Pull Request on GitHub and merge after review
```
