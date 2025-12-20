# docker-templates
A place for me to publish my Unraid docker templates for consumption on Unraid servers.

## Overview
This repository contains custom Docker templates designed specifically for Unraid servers. Each template is carefully crafted to provide easy deployment and management of game servers and applications.

## Available Templates

### MattyStacks
A collection of game server templates and applications.

#### Foundry
A dedicated server template for Foundry, a multiplayer factory-building game (Steam App ID: 2915550).

**Key Features:**
- Automatic server updates via SteamCMD
- Configurable server settings through environment variables
- Persistent storage for game files and saves
- Support for multiple server instances
- Based on ich777's proven steamcmd container structure

**Template Location:** `MattyStacks/Foundry.xml`

For detailed configuration options and setup instructions, see the [MattyStacks README](MattyStacks/README.md).

## How to Use

### Installing from Community Applications (CA)
Once this repository is added to Community Applications, you can install templates directly from the Apps tab in Unraid.

### Manual Installation
1. In your Unraid server, navigate to **Settings** → **Docker**
2. Under "Template repositories", add this URL:
   ```
   https://github.com/MattyStacks/docker-templates
   ```
3. Go to the **Docker** tab and click **"Add Container"**
4. Select the template from the dropdown menu
5. Configure the paths and settings as needed
6. Click **"Apply"** to deploy

## Contributing
This is a personal collection, but feedback and suggestions are welcome!

## Credits
Template structure inspired by ich777's excellent game server Docker templates.
