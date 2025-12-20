# MattyStacks Docker Templates

This directory contains Unraid Docker templates for various game servers and applications. Currently focused on game servers with plans to expand to additional services.

## Current Status

I'm building a collection of Docker templates for Unraid, starting with game servers that I personally use. The first template is for Foundry, and many more will follow!

## Available Templates

### Foundry
A dedicated server template for Foundry, a multiplayer factory-building and automation game where you explore, mine resources, and build automated production chains.

**Steam App ID:** 2915550  
**Container Image:** `ghcr.io/mattystacks/steamcmd:foundry`  
**Template File:** `Foundry.xml`

#### Features:
- Based on ich777's steamcmd container structure
- Automatic server updates via SteamCMD
- Configurable server settings via environment variables
- Persistent storage for game files and saves
- Port forwarding for multiplayer connectivity

#### Default Configuration:
- **Game Port:** 3724 (UDP)
- **Query Port:** 27015 (UDP)
- **Max Players:** 4
- **Autosave Interval:** 300 seconds (5 minutes)
- **Pause When Empty:** Enabled

#### Quick Start:
1. Add the template URL to your Unraid server
2. Deploy the Foundry container
3. Configure server name, world name, and optional password
4. Start the container (first startup will download game files)
5. Connect to your server using the game client

#### Implementation Details:
- **Base Image:** Built on the steamcmd container architecture
- **Auto-Updates:** Server files automatically update on container restart
- **Multi-Instance Support:** Run multiple servers by using different `serverfiles` directories while sharing a single `steamcmd` directory
- **Resource Efficiency:** SteamCMD files are shared across instances to save disk space

#### Important Notes:
- First startup may take 10-15 minutes as it downloads the dedicated server files from Steam (~1-2 GB)
- The server will automatically check for and install updates when restarted
- Container uses `--restart=unless-stopped` policy for automatic recovery
- Based on ich777's proven steamcmd container structure for reliability

#### Server Configuration Variables:

| Variable | Description | Default |
|----------|-------------|---------|
| GAME_ID | Steam App ID for Foundry Dedicated Server | 2915550 |
| SERVER_NAME | Name of your server | Foundry Docker Server |
| SERVER_WORLD_NAME | Name of the world/save | MyWorld |
| MAP_SEED | Map seed for world generation | _(random)_ |
| SERVER_PASSWORD | Server password (optional) | _(empty)_ |
| SERVER_IS_PUBLIC | List server publicly (true/false) | true |
| SERVER_MAX_PLAYERS | Maximum number of players | 4 |
| GAME_PORT | Main game port | 3724 |
| QUERY_PORT | Query port for server browser | 27015 |
| PAUSE_WHEN_EMPTY | Pause server when no players connected | true |
| AUTOSAVE_INTERVAL | Autosave interval in seconds | 300 |

#### Port Forwarding:
Make sure to forward the following ports on your router:
- **UDP 3724** - Game traffic
- **UDP 27015** - Server query/browser

#### Storage Locations:
- `/mnt/user/appdata/steamcmd` - SteamCMD installation (shared between servers)
- `/mnt/user/appdata/foundry` - Server files and world saves

---

## Installation

To use these templates in your Unraid server:

1. Navigate to **Docker** tab in Unraid
2. Scroll to the bottom and click **"Add Container"**
3. In the template dropdown, select your desired template
4. Configure the paths and settings as needed
5. Click **"Apply"** to create and start the container

## Coming Soon

More templates are in development! Stay tuned for additional game servers and applications.

---

## Credits

These templates are based on the excellent work by [ich777](https://github.com/ich777/docker-templates), who has created a comprehensive collection of game server Docker templates for Unraid.

## Support

For issues specific to this template, please create an issue on the [GitHub repository](https://github.com/MattyStacks/docker-templates).

Additional resources:
- [Foundry Official Website](https://www.foundry-game.com/)
- [Foundry Community Discord](https://discord.gg/foundry)
