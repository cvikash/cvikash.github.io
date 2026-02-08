# Local Preview Guide

This guide will help you preview your website locally before pushing to GitHub.

## Prerequisites

1. **Ruby** (version 2.5 or higher)
   - Check if you have Ruby: `ruby --version`
   - If not installed, install via Homebrew: `brew install ruby`

2. **Bundler** (Ruby gem manager)
   - Install: `gem install bundler`

## Setup Instructions

1. **Navigate to your project directory:**
   ```bash
   cd /Users/vchoudhary/Desktop/Personal_website/cvikash.github.io
   ```

2. **Install dependencies:**
   ```bash
   bundle install
   ```
   This will install all the gems specified in your `Gemfile`, including Jekyll and the Minimal Mistakes theme.

3. **Start the local server:**
   ```bash
   bundle exec jekyll serve
   ```

4. **View your site:**
   - Open your browser and go to: `http://localhost:4000`
   - The site will automatically reload when you make changes to files

## Useful Commands

- **Start server with drafts:** `bundle exec jekyll serve --drafts`
  - This will show draft posts (files in `_drafts/` folder)

- **Build without serving:** `bundle exec jekyll build`
  - Creates the `_site/` folder with the generated site

- **Incremental build (faster):** `bundle exec jekyll serve --incremental`
  - Only rebuilds changed files (faster for large sites)

## Troubleshooting

### Port already in use
If port 4000 is busy, use a different port:
```bash
bundle exec jekyll serve --port 4001
```

### Dependencies issues
If you get errors about missing gems:
```bash
bundle update
```

### GitHub Pages metadata warnings
These warnings are normal when running locally and won't affect your site. They're just informational messages about GitHub API authentication.

## Making Changes

1. Edit any file (HTML, Markdown, CSS, etc.)
2. Save the file
3. Jekyll will automatically rebuild
4. Refresh your browser to see changes

## Before Pushing to GitHub

1. Stop the local server (Ctrl+C)
2. Test that the site builds without errors:
   ```bash
   bundle exec jekyll build
   ```
3. Commit and push your changes:
   ```bash
   git add .
   git commit -m "Your commit message"
   git push
   ```

Your site will be live at: `https://cvikash.github.io` (or your GitHub Pages URL)

