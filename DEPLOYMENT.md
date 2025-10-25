# Deployment Guide - GitHub Pages Hosting

This guide will help you deploy your Hall Seat Management System to GitHub Pages for free hosting.

## Quick Setup (Recommended)

### Option 1: Fork the Repository
1. Go to [https://github.com/Shaharia223/PolitixPlume](https://github.com/Shaharia223/PolitixPlume)
2. Click "Fork" button (top right)
3. In your forked repository, go to Settings > Pages
4. Under "Source", select "Deploy from a branch"
5. Select "main" branch and "/ (root)" folder
6. Click "Save"
7. Your site will be available at: `https://yourusername.github.io/PolitixPlume/`

### Option 2: Upload to New Repository
1. Create a new repository on GitHub
2. Upload all files from this folder to the repository
3. Enable GitHub Pages in repository settings
4. Your site will be available at: `https://yourusername.github.io/repositoryname/`

## Detailed Setup Steps

### 1. Create GitHub Repository

1. **Sign in to GitHub**
   - Go to [https://github.com](https://github.com)
   - Sign in or create an account

2. **Create New Repository**
   - Click "+" icon > "New repository"
   - Repository name: `hall-seat-management` (or any name)
   - Description: "Hall Seat Allocation Management System"
   - Make it Public (required for free GitHub Pages)
   - Check "Add a README file"
   - Click "Create repository"

### 2. Upload Your Files

#### Method A: Web Interface (Easier)
1. In your new repository, click "uploading an existing file"
2. Drag and drop all files from this folder
3. Write commit message: "Initial upload of Hall Seat Management System"
4. Click "Commit changes"

#### Method B: Git Command Line
```bash
# Clone your repository
git clone https://github.com/yourusername/repositoryname.git
cd repositoryname

# Copy all files to this directory
# (copy index.html, README.md, etc.)

# Add and commit files
git add .
git commit -m "Initial upload of Hall Seat Management System"
git push origin main
```

### 3. Enable GitHub Pages

1. **Go to Repository Settings**
   - Click "Settings" tab in your repository
   - Scroll down to "Pages" section

2. **Configure Source**
   - Under "Source": Select "Deploy from a branch"
   - Branch: Select "main"
   - Folder: Select "/ (root)"
   - Click "Save"

3. **Wait for Deployment**
   - GitHub will show: "Your site is published at https://yourusername.github.io/repositoryname/"
   - Initial deployment takes 1-10 minutes

### 4. Configure Google Sheets (Optional)

If you want to use Google Sheets integration:

1. **Set up Google Sheets API** (see GOOGLE_SHEETS_SETUP.md)
2. **Edit Configuration**
   - In your repository, click on `index.html`
   - Click the pencil icon to edit
   - Find the `GOOGLE_SHEETS_CONFIG` section
   - Update with your API key and spreadsheet ID
   - Commit changes

3. **Test Integration**
   - Visit your live site
   - Click "Google Sheets Setup" for detailed instructions

## Custom Domain (Optional)

### Using Your Own Domain
1. **Purchase Domain** (from GoDaddy, Namecheap, etc.)
2. **Configure DNS**
   - Add CNAME record pointing to `yourusername.github.io`
3. **Update GitHub Settings**
   - In Pages settings, add your custom domain
   - Enable "Enforce HTTPS"

### Free Subdomain Options
- Use GitHub's provided URL: `yourusername.github.io/repositoryname`
- Or use services like Netlify/Vercel for custom subdomains

## Automatic Deployment

The included GitHub Actions workflow (`.github/workflows/deploy.yml`) automatically deploys your site when you push changes to the main branch.

### How it Works:
1. You push changes to main branch
2. GitHub Actions runs the deployment workflow
3. Your site updates automatically within minutes

### Manual Deployment:
If automatic deployment doesn't work:
1. Go to Actions tab in your repository
2. Click "Deploy to GitHub Pages"
3. Click "Run workflow" > "Run workflow"

## File Structure

Your repository should contain:
```
├── index.html                 # Main application file
├── README.md                 # Documentation
├── GOOGLE_SHEETS_SETUP.md    # Google Sheets integration guide
├── DEPLOYMENT.md             # This file
├── sample-data-template.csv  # Sample data for Google Sheets
└── .github/
    └── workflows/
        └── deploy.yml        # Auto-deployment configuration
```

## Updating Your Site

### Method 1: Web Interface
1. Navigate to the file you want to edit in GitHub
2. Click the pencil icon
3. Make changes
4. Commit changes
5. Site updates automatically

### Method 2: Git Command Line
```bash
# Make changes to files locally
# Then:
git add .
git commit -m "Description of changes"
git push origin main
```

### Method 3: GitHub Desktop
1. Download GitHub Desktop app
2. Clone your repository
3. Make changes locally
4. Commit and push through the app

## Troubleshooting

### Common Issues

1. **Site Not Loading**
   - Check if repository is public
   - Verify Pages is enabled in settings
   - Wait 10-15 minutes for initial deployment

2. **404 Error**
   - Ensure `index.html` is in root directory
   - Check file names are correct
   - Verify Pages source is set to "main" branch

3. **CSS/JS Not Loading**
   - Check file paths are relative (no leading /)
   - Ensure all files are uploaded correctly
   - Check browser console for errors

4. **Google Sheets Not Working**
   - Verify API key is configured correctly
   - Check CORS settings in Google Cloud Console
   - Ensure spreadsheet is publicly accessible

### Debug Steps
1. **Check Repository**
   - Verify all files are present
   - Check file names and structure

2. **Check Pages Settings**
   - Confirm source branch is correct
   - Verify custom domain settings (if used)

3. **Check Actions**
   - Go to Actions tab
   - Look for failed deployments
   - Check error logs

4. **Test Locally**
   - Download files and test locally
   - Use browser developer tools

## Performance Optimization

### Enable GitHub Pages Features
- **HTTPS**: Always enable (free SSL certificate)
- **Custom 404**: Create `404.html` for better error handling

### Optimize Files
- Minimize large images
- Use compressed assets when possible
- Consider CDN for external libraries

### Monitor Usage
- GitHub Pages has usage limits
- 100GB bandwidth per month (generous for most sites)
- 1GB repository size limit

## Security Considerations

### API Keys
- Never commit API keys to public repositories
- Use GitHub Secrets for sensitive data
- Consider using environment variables

### Data Protection
- Student data should be anonymized for public demos
- Use generic names for public repositories
- Consider private repositories for real data

### Access Control
- Repository visibility affects site visibility
- Public repos = public websites
- Private repos need GitHub Pro for Pages

## Next Steps

1. **Test Your Site**
   - Visit your GitHub Pages URL
   - Test all functionality
   - Check mobile responsiveness

2. **Customize Content**
   - Update hall information
   - Modify color schemes
   - Add your institution's branding

3. **Set Up Google Sheets**
   - Follow GOOGLE_SHEETS_SETUP.md guide
   - Test real-time data synchronization

4. **Share Your Site**
   - Share URL with administrators
   - Train users on Google Sheets editing
   - Document any customizations

## Support Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Custom Domain Setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

---

**Last Updated**: October 2025  
**Need Help?**: Create an issue in the GitHub repository