# GitHub Pages Site - Process Documentation

## Overview

This document outlines the setup and ongoing process for maintaining our JSON-powered GitHub Pages site. The site automatically deploys when changes are pushed to the `main` branch.

## Project Structure

```
githubPage/
├── index.html              # Main HTML page (loads content from JSON)
├── content/
│   └── pages.json          # Content file (edit this to update site)
├── images/                 # Store all images here
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions auto-deployment
├── docs/
│   └── process.md          # This document
└── README.md               # Setup instructions
```

## Initial Setup (Completed)

### 1. Repository Setup
- Created repository: `bernokl/githubPage`
- Configured GitHub Pages to use GitHub Actions
- Set up automatic deployment workflow

### 2. Core Files Created
- **index.html**: Main page with JavaScript to load JSON content
- **content/pages.json**: JSON structure for site content
- **.github/workflows/deploy.yml**: Auto-deployment workflow
- **images/**: Folder for storing images

### 3. Features Implemented
- ✅ JSON-based content management
- ✅ Image support with responsive styling
- ✅ Hover tooltips for images and text
- ✅ Cache-busting to prevent browser caching
- ✅ Auto-deployment on push to main branch

## Content Structure

### JSON Format (`content/pages.json`)

```json
{
  "title": "Site Title",
  "description": "Site description",
  "sections": [
    {
      "id": "unique-id",
      "title": "Section Title",
      "content": "Section content text",
      "image": "images/filename.jpg",           // Optional
      "tooltip": "Tooltip text for image",      // Optional (for images)
      "contentTooltip": "Tooltip for text"      // Optional (for text)
    }
  ]
}
```

### Field Descriptions
- **id**: Unique identifier for the section
- **title**: Section heading
- **content**: Main text content
- **image**: Path to image (relative to site root, e.g., `images/photo.jpg`)
- **tooltip**: Text shown when hovering over the image
- **contentTooltip**: Text shown when hovering over the content text

## Adding Images

### Method 1: Store in Repository (Recommended)

1. **Copy image to images folder:**
   ```bash
   cp /path/to/image.jpg ~/projects/githubPage/images/
   ```

2. **Reference in JSON:**
   ```json
   "image": "images/image.jpg"
   ```

3. **Commit and push:**
   ```bash
   git add images/image.jpg content/pages.json
   git commit -m "Add new image"
   git push origin main
   ```

### Method 2: External URLs

Use direct image URLs (not Google search URLs):
```json
"image": "https://example.com/image.jpg"
```

## Git Workflow

### Creating and Using Branches

```bash
# 1. Create and switch to a new branch
git checkout -b feature-name

# 2. Make your changes
# (edit files, add images, etc.)

# 3. Stage your changes
git add .

# 4. Commit with descriptive message
git commit -m "Description of changes"

# 5. Push the branch to GitHub
git push origin feature-name

# 6. Create a Pull Request on GitHub (via web interface)

# To switch back to main branch:
git checkout main

# To see all branches:
git branch -a

# To delete a local branch (after merging):
git branch -d feature-name
```

### Standard Workflow

1. **Create feature branch** → `git checkout -b feature-name`
2. **Make changes** → Edit files, add images
3. **Commit changes** → `git add . && git commit -m "message"`
4. **Push branch** → `git push origin feature-name`
5. **Create PR** → On GitHub, create Pull Request
6. **Review & Merge** → After review, merge to main
7. **Auto-deploy** → Site automatically updates

### Direct to Main (Quick Updates)

For quick content updates, you can push directly to main:

```bash
git add .
git commit -m "Update content"
git push origin main
```

The site will automatically rebuild and deploy.

## Updating Site Content

### Quick Content Update

1. Edit `content/pages.json`
2. Commit and push:
   ```bash
   git add content/pages.json
   git commit -m "Update site content"
   git push origin main
   ```

### Adding New Section

1. Add new section object to `sections` array in `pages.json`
2. Follow the JSON structure above
3. Commit and push

### Adding Images with Tooltips

1. Add image file to `images/` folder
2. Update JSON:
   ```json
   {
     "id": "new-section",
     "title": "New Section",
     "content": "Content here",
     "image": "images/new-image.jpg",
     "tooltip": "Hover text for image"
   }
   ```
3. Commit and push

## Troubleshooting

### Images Not Showing
- Check image path is correct (relative to site root)
- Ensure image file is committed to repository
- Verify image file exists in `images/` folder
- Check browser console for 404 errors

### Changes Not Appearing
- Hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R)
- Check GitHub Actions workflow ran successfully
- Verify changes were pushed to `main` branch
- Wait a few minutes for GitHub Pages to update

### JSON Syntax Errors
- Validate JSON at https://jsonlint.com/
- Check for missing commas, quotes, or brackets
- Ensure no duplicate field names

## Current Site Content

### Sections Configured
1. **Hero Section** (`id: "hero"`)
   - Image: `images/happy_man.jpeg`
   - Tooltip: "This is the exited/happy man image!"

2. **About Section** (`id: "about"`)
   - Image: `images/thinking_person.jpeg`
   - Tooltip: "This is the thinking person image!"
   - Content tooltip available

3. **Confused Section** (`id: "confused"`)
   - Image: `images/Screenshot_20260304_205105.png`
   - Tooltip: "This is your screenshot!"

## Best Practices

1. **Always validate JSON** before committing
2. **Use descriptive commit messages**
3. **Test locally** if possible before pushing
4. **Use branches** for major changes
5. **Keep images optimized** (compress large images)
6. **Use meaningful section IDs** (no spaces, lowercase)

## Future Enhancements

Potential improvements:
- [ ] Multiple pages support
- [ ] Slack webhook integration for content updates
- [ ] AI agent to convert natural language to JSON
- [ ] Image upload interface
- [ ] Content preview before deployment
- [ ] Version history/rollback

## Resources

- **GitHub Pages Docs**: https://docs.github.com/en/pages
- **JSON Validator**: https://jsonlint.com/
- **Git Cheat Sheet**: https://education.github.com/git-cheat-sheet-education.pdf

---

**Last Updated**: March 4, 2026  
**Maintained By**: Bernokl & Mr Matt
