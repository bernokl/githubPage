# Image Path Fix

## Issue
Images were not showing up correctly in the Hugo site.

## Solution Applied
Updated the image path in `layouts/index.html` to use Hugo's `absURL` function which properly handles the baseURL for GitHub Pages.

## How It Works

- **Static files location**: `static/images/happy_man.jpeg`
- **In JSON**: `"image": "images/happy_man.jpeg"`
- **In template**: `{{ (printf "/%s" .image) | absURL }}`
- **Result**: `https://bernokl.github.io/githubPage/images/happy_man.jpeg`

## Testing

1. **Local testing**:
   ```bash
   hugo server
   # Visit http://localhost:1313
   # Images should work at http://localhost:1313/images/...
   ```

2. **Production**:
   - After deployment, images will be at: `https://bernokl.github.io/githubPage/images/...`
   - The `absURL` function automatically prepends the baseURL from `config.toml`

## If Images Still Don't Work

1. **Check baseURL in config.toml**:
   - Should be: `baseURL = 'https://bernokl.github.io/githubPage/'`
   - Must have trailing slash for project sites

2. **Verify images are in static/images/**:
   ```bash
   ls -la static/images/
   ```

3. **Check built output**:
   ```bash
   hugo
   ls -la public/images/
   ```

4. **Alternative fix** (if absURL doesn't work):
   Change template to:
   ```html
   <img src="{{ .Site.BaseURL }}{{ .image }}" alt="{{ .title }}" class="section-image tooltip-image">
   ```
