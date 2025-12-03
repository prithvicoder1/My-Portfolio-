# Deployment Guide

## Fixed Issues:
1. ✅ Updated `vercel.json` to properly serve static files
2. ✅ URL-encoded all file paths with spaces and special characters
3. ✅ Configured proper routing for assets

## Deployment Steps:

### For Vercel:
1. Make sure all files are in the root directory:
   - `index.html`
   - `vercel.json`
   - All image files (`.png`, `.jpg`, `.jpeg`)
   - All PDF files (`.pdf`)

2. Deploy using one of these methods:

   **Option A: Vercel CLI**
   ```bash
   npm i -g vercel
   vercel
   ```

   **Option B: Vercel Dashboard**
   - Go to https://vercel.com
   - Click "New Project"
   - Import your repository or drag & drop the folder
   - Vercel will automatically detect the configuration

   **Option C: GitHub Integration**
   - Push your code to GitHub
   - Connect your GitHub repo to Vercel
   - Vercel will auto-deploy on every push

### For Other Platforms:

**Netlify:**
- Create a `netlify.toml` file (optional, Netlify auto-detects)
- Drag & drop your folder to Netlify dashboard

**GitHub Pages:**
- Push to GitHub
- Go to Settings > Pages
- Select source branch (usually `main` or `master`)
- Your site will be at: `https://yourusername.github.io/repo-name/`

## Important Notes:
- All file paths with spaces have been URL-encoded (e.g., `Python for the web .jpg` → `Python%20for%20the%20web%20.jpg`)
- The `vercel.json` file is configured to serve static assets properly
- Make sure all image and PDF files are included in your deployment

## Troubleshooting NOT_FOUND Error:

If you see `NOT_FOUND` error on Vercel:

### Solution 1: Set Project Root (IMPORTANT!)
1. Go to your Vercel project dashboard
2. Click on **Settings** → **General**
3. Scroll to **Root Directory**
4. Make sure it's set to **`/`** (root) or leave it empty
5. If you deployed from a subfolder, set it to that folder path

### Solution 2: Use Vercel CLI with Correct Settings
```bash
# Install Vercel CLI
npm i -g vercel

# Navigate to your project
cd "/Users/prithvivijay/Desktop/My Protfolio "

# Deploy (answer prompts)
vercel

# When asked:
# - Set up and deploy? Yes
# - Which scope? (select your account)
# - Link to existing project? No
# - Project name? portfolio (or any name)
# - Directory? ./
# - Override settings? No
```

### Solution 3: Manual Upload via Dashboard
1. Go to https://vercel.com/dashboard
2. Click **Add New** → **Project**
3. Click **Browse** and select your entire folder
4. **IMPORTANT**: In project settings, make sure:
   - **Framework Preset**: "Other" or "Static Site"
   - **Root Directory**: Leave empty or set to `/`
   - **Build Command**: Leave empty
   - **Output Directory**: Leave empty
5. Click **Deploy**

### Solution 4: Check File Structure
Make sure your files are structured like this:
```
My Protfolio /
├── index.html          ← Must be in root
├── vercel.json         ← Configuration
├── package.json        ← Helps Vercel detect project
├── photo.png
├── resume.pdf
└── (all other files)
```

### Solution 5: Delete and Redeploy
1. Delete the project from Vercel dashboard
2. Create a new project
3. Upload all files again
4. Make sure **Framework Preset** is set to **"Other"**

## Other Troubleshooting:
- If you see "Page Not Found": Check that `index.html` is in the root directory
- If images don't load: Verify file names match exactly (case-sensitive)
- If certificates don't open: Check browser console for errors
- If deployment fails: Check Vercel logs in the dashboard for specific errors

