# Cowork Plugins Marketplace POC

A proof-of-concept for a Claude Code plugin marketplace, demonstrating how plugins and skills can be structured, registered, and discovered.

## Project Structure

```
.claude-plugin/
  marketplace.json        # Plugin registry — lists all available plugins
hello/
  skills/
    say-hello/
      SKILL.md            # Skill definition (metadata + content)
.claude/
  settings.local.json     # Local Claude Code permissions
```

## How It Works

1. **Marketplace Registry** — `.claude-plugin/marketplace.json` acts as the central catalog of available plugins, each pointing to a local directory.
2. **Plugins** — Each plugin lives in its own top-level directory (e.g., `hello/`) and contains one or more skills.
3. **Skills** — Defined as `SKILL.md` files with YAML front matter (`name`, `description`) and markdown body content.

## Adding a New Plugin

1. Create a directory for your plugin at the project root:
   ```
   my-plugin/
     skills/
       my-skill/
         SKILL.md
   ```

2. Define your skill in `SKILL.md`:
   ```markdown
   ---
   name: my-skill
   description: A short description of what the skill does
   ---

   Skill content and instructions go here.
   ```

3. Register the plugin in `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "my-plugin",
     "source": "./my-plugin",
     "description": "What my plugin does"
   }
   ```

## Included Plugins

### hello / say-hello

Generates a personalized greeting for a given name.

**Usage:** Provide a name and the skill produces a warm, professional greeting.

| Input | Output |
|-------|--------|
| Mike  | "Hello, Mike! Great to meet you. Welcome aboard — if there's anything you need, don't hesitate to ask!" |

## Getting Started

```bash
git clone git@github.com:geneweng/cowork-plugins-marketplace-poc.git
cd cowork-plugins-marketplace-poc
```

No dependencies to install — the project is pure configuration and markdown.
