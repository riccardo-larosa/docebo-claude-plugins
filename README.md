# Docebo Plugin Marketplace

A private plugin marketplace for Claude Desktop with Docebo-specific plugins.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| **docebo-lms** | Manage Docebo LMS — enroll users, track progress, generate reports, search courses |

## Setup

### 1. Users add the marketplace

In Claude Desktop, run:

```
/plugin marketplace add riccardo-larosa/docebo-claude-plugins
```

### 2. Users install a plugin

```
/plugin install docebo-lms@docebo-marketplace
```

## Requirements

- Users must have the **Docebo MCP connector** enabled in Claude Desktop

## Adding More Plugins

1. Create a new plugin directory under `plugins/`
2. Add an entry to `.claude-plugin/marketplace.json`
3. Commit and push
