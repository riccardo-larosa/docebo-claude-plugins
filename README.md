# Docebo Plugin Marketplace

A private plugin marketplace for Claude Desktop with Docebo-specific plugins.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| **docebo-lms** | Manage Docebo LMS — enroll users, track progress, generate reports, search courses |

## Setup

### 1. Push this repo to GitHub (private)

```bash
cd docebo-claude-plugins
git init
git add .
git commit -m "Initial marketplace with docebo-lms plugin"
gh repo create docebo/claude-plugins --private --source=. --push
```

### 2. Users add the marketplace

In Claude Desktop, run:

```
/plugin marketplace add docebo/claude-plugins
```

### 3. Users install a plugin

```
/plugin install docebo-lms@docebo-marketplace
```

## Requirements

- Users must have the **Docebo MCP connector** enabled in Claude Desktop
- The repo must remain **private** (company policy)

## Adding More Plugins

1. Create a new plugin directory under `plugins/`
2. Add an entry to `.claude-plugin/marketplace.json`
3. Commit and push
