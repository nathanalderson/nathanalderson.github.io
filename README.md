# nathanalderson.github.io

Source code for https://nathanalderson.com

## Development Setup

### Prerequisites

This project uses [asdf](https://asdf-vm.com/) to manage Node.js and Ruby versions.

1. **Install asdf** (if not already installed): see https://asdf-vm.com/guide/getting-started.html

2. **Install ASDF plugins** for Node.js and Ruby:
   ```bash
   asdf plugin add nodejs
   asdf plugin add ruby
   ```

3. **Install the required versions** (defined in `.tool-versions`):
   ```bash
   asdf install
   ```
   
### Installing Dependencies

1. **Install Ruby dependencies**:
   ```bash
   bundle install
   ```
   
   This installs Jekyll and all required gems defined in the `Gemfile`.

2. **Install Node.js dependencies**:
   ```bash
   npm install
   ```
   
   This installs Tailwind CSS, Alpine.js, esbuild, and related packages.

## Development Workflow

### Running the Development Server

You'll need to run **three processes** simultaneously for local development:

#### 1. JavaScript Bundler Watcher

In one terminal, run the esbuild watcher to automatically rebuild JavaScript when you make changes:

```bash
npm run build:js:watch
```

This watches `assets/js/app.js` and bundles it with Alpine.js to `assets/js/app.bundle.js`.

#### 2. Tailwind CSS Watcher

In another terminal, run the Tailwind watcher to automatically rebuild CSS when you make changes:

```bash
npm run build:css:watch
```

This watches `main.css` for changes and compiles it to `output.css`.

#### 3. Jekyll Development Server

In a third terminal, run the Jekyll development server:

```bash
bundle exec jekyll serve
```

The site will be available at `http://localhost:4002`.

The Jekyll server will automatically rebuild when you change files, and you can refresh your browser to see the changes.

## Deployment

This site is configured to deploy to GitHub Pages via GitHub Actions. The workflow is defined in `.github/workflows/jekyll-gh-pages.yml`.

When you push to the `main` branch, the site will automatically build and deploy.
