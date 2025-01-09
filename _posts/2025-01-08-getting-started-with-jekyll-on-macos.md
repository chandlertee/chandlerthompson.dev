---
title: Getting Started with Jekyll on macOS
description: A step-by-step guide to setting up Ruby, Bundler, and Jekyll on macOS
  using Homebrew and chruby for your static site needs.
layout: post
categories:
- Developer Tools
tags:
- mac-os
- jekyll
- developer-tools
date: 2025-01-08 18:03 -0600
---
So you want to set up a sleek new Jekyll site, but you’re staring at your terminal wondering why Ruby, Bundler, and a bunch of configuration files are involved. Fear not, intrepid site-builder, because I’ve got your back. Let’s walk through how to set up Ruby using `chruby` and Homebrew, install Bundler, and get Jekyll running smoothly on macOS.

---

## Why Ruby, Bundler, and chruby?

Before diving in, here’s the TL;DR on why you need these tools:

- **Ruby**: Jekyll is written in Ruby, so we need Ruby installed to run it.
- **chruby**: A lightweight Ruby version manager that makes switching between Ruby versions a breeze.
- **Bundler**: Manages Ruby gem dependencies so your Jekyll site runs the same way on every machine.
- **Homebrew**: A macOS package manager that simplifies the installation of all the above.

---

## Installing Ruby with Homebrew and chruby

### Step 1: Install Homebrew

If you don’t already have Homebrew, install it. I have an [installation guide](/posts/installing-homebrew-on-macos/). The short version is paste the below command into your terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, make sure Homebrew is set up:

```bash
brew doctor
brew update
```

### Step 2: Install chruby and ruby-install

Use Homebrew to install `chruby` and `ruby-install`:

```bash
brew install chruby ruby-install
```

### Step 3: Install Ruby

Install the latest stable Ruby version supported by Jekyll:

```bash
ruby-install ruby 3.3.5
```

Once installed, configure your shell to use `chruby`. Add the following lines to your shell’s configuration file (e.g., `~/.zshrc` for Zsh users or `~/.bash_profile` for Bash users):

```sh
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.3.5" >> ~/.zshrc
```

Replace `.zshrc` with `.bash_profile` if you use Bash. Restart your terminal to apply the changes, and verify the Ruby installation:

```bash
ruby -v
```

You should see something like `ruby 3.3.5 (2024-09-03 revision ef084cc8f4)`.

---

## Installing Bundler

Bundler is essential for managing Jekyll’s dependencies. Install it globally:

```bash
gem install bundler
```

To confirm the installation:

```bash
bundle -v
```

---

## Setting Up a Minimal Jekyll Site

### Step 1: Install Jekyll

Now that Ruby and Bundler are set up, install Jekyll:

```bash
gem install jekyll
```

### Step 2: Create a New Jekyll Site

Navigate to the directory where you want your site and run:

```bash
jekyll new my-awesome-site
```

This command generates a new Jekyll site with a basic configuration.

### Step 3: Run the Site Locally

Navigate into your site’s directory:

```bash
cd my-awesome-site
```

Install the site’s dependencies using Bundler:

```bash
bundle install
```

Start the local Jekyll server:

```bash
bundle exec jekyll serve --livereload
```

The `--livereload` option automatically refreshes your browser when you make changes to the source files, enhancing your development workflow. Visit `http://localhost:4000` in your browser, and boom! Your site is live locally.

---

## Customizing Jekyll Configuration

Your site’s configuration lives in `_config.yml`. Here’s an example of how to customize the default settings provided by Jekyll’s Minima theme:

```yaml
title: "My Awesome Blog"
email: "me@example.com"
description: >-
  A personal blog about tech, life, and other adventures.
baseurl: "" # The subpath of your site, e.g., /blog
url: "https://myawesomeblog.com" # The base hostname & protocol for your site

twitter_username: my_twitter_handle
github_username:  my_github_username

# Build settings
theme: minima
plugins:
  - jekyll-feed
```

### Key Settings Explained:

- **`title`**: The title of your site, which appears in the browser tab and header.
    
- **`email`**: Your email address, displayed in the footer if configured.
    
- **`description`**: A brief description of your site for SEO and metadata purposes.
    
- **`baseurl`** and **`url`**: Essential for setting up the correct paths for assets and links when deploying your site.
    
- Social Links (**`twitter_username`**, **`github_username`**): These are used by the Minima theme to link to your social profiles in the footer.
    

Make sure to save your changes and restart the Jekyll server to apply them.

For more details on configuration options, check out the [Jekyll Configuration documentation](https://jekyllrb.com/docs/configuration/).

---

## Version Control with Git

One of the great things about Jekyll is there’s no database. All content and site structure are files that a Git repository can version. Using a repository is optional but recommended. You can learn more about using Git by reading the [Git Handbook](https://guides.github.com/introduction/git-handbook/).

To initialize a Git repository in your project directory:

```bash
git init
git add .
git commit -m "Initial commit"
```

This setup allows you to track changes, collaborate with others, and deploy your site efficiently.

---

## Troubleshooting Tips

1. **Ruby Version Issues**: Ensure you’re using the correct Ruby version with `chruby`.
2. **Permission Errors**: Use a Ruby version installed in your home directory to avoid `sudo`.
3. **Dependency Conflicts**: Delete `Gemfile.lock` and re-run `bundle install`.
4. **LiveReload Not Working**: Ensure you’re using the `--livereload` flag when running the server. If issues persist, check for browser extensions or firewall settings that might block LiveReload.

---

## Additional Resources

- [Jekyll Official Documentation](https://jekyllrb.com/docs/)

And there you have it! A fully functioning Jekyll setup ready for customization. Now go forth and build something amazing—whether it’s a blog, a portfolio, or a cat appreciation site (highly recommended). What do you plan to build?
