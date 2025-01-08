# Local Development Guide

This guide will help you set up and run this TIL site locally on your machine.

## Prerequisites

Before you begin, ensure you have the following installed:

### For macOS

1. **Install Homebrew** (if not already installed)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Ruby** (macOS comes with Ruby, but it's recommended to use a version manager)
   ```bash
   # Install rbenv
   brew install rbenv

   # Set up rbenv in your shell
   rbenv init

   # Install Ruby 3.2.2
   rbenv install 3.2.2
   rbenv global 3.2.2
   ```

3. **Install Bundler**
   ```bash
   gem install bundler
   ```

### For Windows

1. Download and install Ruby+Devkit from [RubyInstaller](https://rubyinstaller.org/downloads/)
2. During installation, check the option to run `ridk install`
3. Open Command Prompt and install Bundler:
   ```bash
   gem install bundler
   ```

### For Linux (Ubuntu/Debian)

1. Install Ruby and development dependencies:
   ```bash
   sudo apt-get update
   sudo apt-get install ruby-full build-essential zlib1g-dev
   ```

2. Install Bundler:
   ```bash
   gem install bundler
   ```

## Setting Up the Project

1. **Clone the repository**
   ```bash
   git clone <your-repository-url>
   cd <repository-name>
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```
   If you encounter any permissions errors, try:
   ```bash
   bundle install --path vendor/bundle
   ```

## Running the Site Locally

1. **Start the Jekyll server**
   ```bash
   bundle exec jekyll serve
   ```
   This will start the server at `http://localhost:4000`

2. **Development options**
   - To enable live reloading:
     ```bash
     bundle exec jekyll serve --livereload
     ```
   - To show draft posts:
     ```bash
     bundle exec jekyll serve --drafts
     ```
   - To specify a different port:
     ```bash
     bundle exec jekyll serve --port 4001
     ```

## Common Issues and Solutions

### Bundler Error
If you see an error about bundler versions:
```bash
bundle update
bundle install
```

### Permission Errors
If you encounter permission errors while installing gems:
```bash
gem install bundler --user-install
bundle install --path vendor/bundle
```

### Port Already in Use
If port 4000 is already in use:
```bash
# Either kill the process using port 4000
lsof -i :4000
kill -9 <PID>

# Or use a different port
bundle exec jekyll serve --port 4001
```

## File Structure

```
.
├── _config.yml          # Site configuration
├── _til/               # TIL posts directory
├── _layouts/           # Layout templates
├── assets/            # CSS, JavaScript, and images
│   ├── css/
│   └── js/
├── index.html         # Homepage
├── search.html        # Search page
└── tags.html          # Tags page
```

## Adding Content

1. Create a new markdown file in `_til/` with the format `YYYY-MM-DD-title.md`
2. Add the front matter:
   ```yaml
   ---
   layout: post
   title: "Your TIL Title"
   date: YYYY-MM-DD
   tags: [tag1, tag2]
   ---
   ```
3. Write your content in markdown below the front matter
4. Save and the site will automatically rebuild

## Testing

1. Check that your post appears on the homepage
2. Verify that tags are working correctly
3. Test the search functionality with your new content
4. Ensure responsive design works on different screen sizes

## Deployment

After testing locally, commit and push your changes:
```bash
git add .
git commit -m "Add new TIL post"
git push origin main
```

GitHub Pages will automatically rebuild and deploy your site.
