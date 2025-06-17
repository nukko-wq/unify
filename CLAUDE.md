# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is "Unify", a WordPress theme based on Automattic's _s (Underscores) starter theme with Tailwind CSS integration. The theme is currently in development and requires completion of the migration from the _s boilerplate.

## Build Commands

### CSS Development
```bash
# Install dependencies
npm install

# Build Tailwind CSS
npm run build

# Watch for changes during development
npm run watch

# Build minified CSS for production
npm run build:minify
```

### PHP Development
```bash
# Install PHP dependencies
composer install

# Check PHP coding standards
composer lint:wpcs

# Check PHP syntax
composer lint:php

# Generate translation files
composer make-pot
```

## Architecture

### Theme Structure
- **functions.php**: Main theme setup and WordPress feature registration
- **inc/**: Modular functionality split into separate files
  - `template-tags.php`: Custom template functions
  - `template-functions.php`: WordPress hooks and filters
  - `customizer.php`: WordPress Customizer integration
  - `custom-header.php`: Custom header functionality
- **template-parts/**: Reusable content templates
- **src/input.css**: Tailwind CSS source file
- **css/style.css**: Compiled CSS output

### CSS Architecture
- Uses Tailwind CSS 4.1.10 with CLI compilation
- Source file: `src/input.css` (contains only `@import "tailwindcss";`)
- Output file: `css/style.css` (auto-generated, in .gitignore)
- No Tailwind configuration file present (using defaults)
- Tailwind classes being used in templates (e.g., `text-2xl font-bold` in header.php)

### PHP Architecture
- Follows WordPress coding standards
- All functions prefixed with `blank_theme_` (needs updating to `unify_`)
- Text domain: `blank_theme` (needs updating to `unify`)
- Minimum PHP version: 5.6

## Current State and Required Updates

### Incomplete Migration from _s
The theme still contains _s boilerplate code that needs updating:

1. **Function Prefixes**: Change all `blank_theme_` to `unify_`
2. **Text Domain**: Update `blank_theme` to `unify` throughout codebase
3. **Constants**: Update `_S_VERSION` and related constants
4. **Translation Files**: Rename `blank_theme.pot` to `unify.pot`
5. **Package Info**: Update composer.json with correct theme information

### Theme Information
Current style.css header shows:
- Theme Name: Unify
- Author: Folder Team
- Version: 1.0.0

## WordPress Integration

### Supported Features
- Post thumbnails
- Custom header
- Title tag support
- Automatic feed links
- Navigation menus
- Custom logo
- HTML5 markup

### Template Hierarchy
Standard WordPress template files:
- `index.php`: Main template
- `single.php`: Single post template
- `page.php`: Page template
- `archive.php`: Archive template
- `search.php`: Search results template
- `404.php`: Error page template

## Development Workflow

### Initial Setup
1. Run `npm install` to install Tailwind CSS dependencies
2. Run `composer install` to install PHP development tools
3. Use `npm run watch` during development for automatic CSS compilation
4. Run `npm run build` before committing changes

### Git Configuration
- `.gitignore` excludes build outputs (`css/style.css`), dependencies, and temporary files
- Only commit source files (`src/input.css`, PHP templates, etc.)

## Key File Locations

- Theme configuration: `functions.php`
- CSS source: `src/input.css`
- CSS output: `css/style.css` (auto-generated)
- Git ignore rules: `.gitignore`
- PHP standards config: `phpcs.xml.dist`
- Composer config: `composer.json`
- Package config: `package.json`