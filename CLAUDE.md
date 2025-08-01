# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based documentation site for Telegram Bot Manager - a SaaS platform for creating and managing Telegram bots. The site is hosted on GitHub Pages and provides user documentation in Russian.

## Key Commands

### Development
```bash
# Install dependencies
bundle install

# Start local development server
bundle exec jekyll serve

# Start with live reload
bundle exec jekyll serve --livereload

# Include drafts in development
bundle exec jekyll serve --drafts

# Build static files
bundle exec jekyll build
```

### Testing
```bash
# Build and check for errors
bundle exec jekyll build

# Check generated site in _site/ directory
```

## Architecture & Structure

### Jekyll Site Structure
- **_config.yml**: Main Jekyll configuration with site metadata, navigation, and plugin settings
- **index.md**: Homepage with platform overview and feature grid
- **quick-start.md**: Installation and setup guide
- **canvas-guide.md**: Complete visual builder documentation
- **api.md**: REST API reference documentation
- **assets/css/style.scss**: Custom styles including buttons, feature grids, alerts, and badges

### Content Organization
- Uses Jekyll's default page structure with Front Matter
- Collections configured for guides with custom permalinks
- Navigation defined in _config.yml with Russian titles
- SEO optimization via jekyll-seo-tag plugin

### Styling System
Available CSS classes:
- Buttons: `.btn`, `.btn-primary`, `.btn-secondary`
- Layout: `.feature-grid`, `.feature-card`
- Alerts: `.alert`, `.alert-info`, `.alert-warning`
- Badges: `.badge`, `.badge-success`

### Deployment
- Automatically deployed to GitHub Pages on commits to main branch
- Uses GitHub Actions for automated Jekyll builds
- Generated files excluded from repository via .gitignore

## Content Guidelines

### Page Structure
Each markdown file requires Front Matter:
```yaml
---
layout: default
title: Page Title
description: SEO description
permalink: /custom-url/
---
```

### Documentation Focus
- Primary audience: Russian-speaking users
- Content covers platform features, Canvas visual builder, and API integration
- Includes practical examples and step-by-step guides
- Multi-tenant SaaS platform with focus on bot management

## Related Repositories
- Main platform: https://github.com/surnin/telegram-bot-manager
- Bot examples: https://github.com/surnin/telegram-bot-examples