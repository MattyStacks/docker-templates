# MattyStacks Docker Templates

This directory contains Unraid Docker templates for various game servers and applications.

## Available Templates

### Foundry
A dedicated server template for the Foundry game (factory-building multiplayer game).

**Steam App ID:** 2915550

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

#### Notes:
- First startup may take a long time as it downloads the dedicated server files from Steam
- The server will automatically update when restarted if a new version is available
- You can run multiple servers by pointing them to different `serverfiles` directories while sharing the same `steamcmd` directory

#### Server Configuration Variables:

| Variable | Description | Default |
|----------|-------------|---------|
| GAME_ID | Steam App ID for Foundry Dedicated Server | 2915550 |
| SRV_NAME | Name of your server | Foundry Docker Server |
| WORLD_NAME | Name of the world/save | MyWorld |
| SRV_PWD | Server password (optional) | _(empty)_ |
| PUBLIC | List server publicly (1=yes, 0=no) | 1 |
| MAX_PLAYERS | Maximum number of players | 4 |
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

## Credits

These templates are based on the excellent work by [ich777](https://github.com/ich777/docker-templates), who has created a comprehensive collection of game server Docker templates for Unraid.

## Support

For issues with the template or container setup, please refer to:
- [ich777's Unraid Forums Support Thread](https://forums.unraid.net/topic/79530-support-ich777-gameserver-dockers/)
- [Foundry Official Documentation](https://www.foundry-game.com/)
- [Foundry Dedicated Server Guide](https://dedicated.foundry-game.com/)
