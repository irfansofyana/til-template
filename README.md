# Today I Learned Template

A GitHub Pages template for creating your own Today I Learned (TIL) website. Document and share your daily learnings in an organized and searchable way.

## Features

- 📝 Write TILs in Markdown
- 🔍 Full-text search functionality
- 🏷️ Tag support with dedicated tag pages
- 📱 Responsive design
- 🚀 Fast and lightweight
- 🐳 Docker support for easy development

## Getting Started

1. Click "Use this template" to create your own repository
2. Update `_config.yml` with your site information:
   - Change `title` and `description`
   - Update `baseurl` to match your repository name
   - Update `url` if using a custom domain

3. Add your TILs in the `_til` directory following the format:
   ```markdown
   ---
   layout: post
   title: "Your TIL Title"
   date: YYYY-MM-DD
   tags: [tag1, tag2]
   ---

   Your content here in Markdown
   ```

4. Enable GitHub Pages in your repository settings:
   - Go to Settings > Pages
   - Set source to `main` branch
   - Save changes

## Local Development

You can run this site either directly on your machine or using Docker.

### Option 1: Using Docker (Recommended)

Prerequisites: [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/)

1. Build and start the container:
```bash
docker-compose up
```

2. Visit `http://localhost:4000` in your browser

The site will automatically rebuild when you make changes to the source files.

To stop the container:
```bash
docker-compose down
```

### Option 2: Direct Installation

#### Prerequisites

#### macOS
```bash
# Install Homebrew if not installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Ruby via rbenv
brew install rbenv
rbenv init
rbenv install 3.2.2
rbenv global 3.2.2

# Install Bundler
gem install bundler
```

#### Windows
1. Download and install Ruby+Devkit from [RubyInstaller](https://rubyinstaller.org/downloads/)
2. During installation, check the option to run `ridk install`
3. Open Command Prompt and run:
```bash
gem install bundler
```

#### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install ruby-full build-essential zlib1g-dev
gem install bundler
```

### Setting Up the Project

1. Clone the repository
```bash
git clone <your-repository-url>
cd <repository-name>
```

2. Install dependencies
```bash
bundle install
```

### Running Locally

1. Start the Jekyll server
```bash
bundle exec jekyll serve
```

2. Visit `http://localhost:4000` in your browser

### Development Options

- Enable live reloading:
```bash
bundle exec jekyll serve --livereload
```
- Show draft posts:
```bash
bundle exec jekyll serve --drafts
```
- Use a different port:
```bash
bundle exec jekyll serve --port 4001
```

### Common Issues

1. **Bundler Error**
```bash
bundle update
bundle install
```

2. **Permission Errors**
```bash
gem install bundler --user-install
bundle install --path vendor/bundle
```

3. **Port Already in Use**
```bash
# Either kill the process using port 4000
lsof -i :4000
kill -9 <PID>

# Or use a different port
bundle exec jekyll serve --port 4001
```

### Docker-specific Issues

1. **Permission Issues**
If you encounter permission issues with Docker:
```bash
sudo chown -R $USER:$USER .
```

2. **Port Conflicts**
If port 4000 is already in use, modify the port mapping in `docker-compose.yml`:
```yaml
ports:
  - "4001:4000"  # Change 4001 to any available port
```

3. **Performance on macOS**
For better performance on macOS, you can add these volume options to `docker-compose.yml`:
```yaml
volumes:
  - .:/app:cached
```

## License

This project is open source and available under the [MIT License](LICENSE).
