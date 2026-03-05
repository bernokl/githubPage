# GitHub Pages JSON-Powered Site

A simple website that uses JSON files for content and automatically deploys to GitHub Pages.

## How It Works

1. **Content Storage**: Website content is stored in `content/pages.json`
2. **Auto-Deploy**: When you push changes to the `main` branch, GitHub Actions automatically deploys to GitHub Pages
3. **Simple Updates**: Just edit the JSON file and push - no HTML knowledge needed!

## Setup Instructions

1. **Enable GitHub Pages**:
   - Go to your repository Settings → Pages
   - Under "Source", select "GitHub Actions"

2. **Edit Content**:
   - Edit `content/pages.json` to change your website content
   - Commit and push your changes
   - The site will automatically rebuild and deploy

## Content Structure

The `content/pages.json` file follows this structure:

```json
{
  "title": "Your Site Title",
  "description": "Your site description",
  "sections": [
    {
      "id": "section-id",
      "title": "Section Title",
      "content": "Section content goes here"
    }
  ]
}
```

## Future Enhancements

- Slack webhook integration for content updates
- AI agent to convert natural language to JSON
- Multiple pages support
- Custom styling options
