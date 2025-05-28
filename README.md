<h1 align="center">
  DreamCrates
</h1>

<p align="center">
  <img src="https://raw.githubusercontent.com/teaminfinitydev/teaminfinitydev/refs/heads/main/img/dreamcrates_banner.svg" alt="OutbreakX Banner" width="800"/>
</p>
<p align="center">
DreamCrates is a feature-rich and highly customizable crate plugin for Minecraft servers running Paper 1.21.1+.
</p>
## Features

- **Multiple Crate Types**: Create unlimited custom crate types with different rarities
- **Animation System**: 5 unique opening animations (Spin, Flicker, Drop, Wheel, CSGO-style)
- **Dual Key System**: Support for both physical and virtual keys
- **Reward System**: Weighted reward system with command execution
- **Visual Effects**: Customizable particles and sounds for each crate
- **Hologram Support**: Display crate names as holograms
- **Preview System**: Let players preview crate contents
- **Daily Rewards**: Built-in daily login crate key rewards
- **Vote Rewards**: Integration with voting plugins
- **Legendary Broadcasts**: Announce when players receive legendary items

## Installation

1. Download the latest version of DreamCrates from [GitHub Releases](https://github.com/yourusername/DreamCrates/releases)
2. Place the JAR file in your server's `plugins` folder
3. Restart your server
4. Edit the configuration files to customize crates and rewards

## Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/crate` | Main command for DreamCrates | `dreamcrates.command` |
| `/crate help` | Shows help information | `dreamcrates.command` |
| `/crate create <name>` | Creates a new crate | `dreamcrates.admin.create` |
| `/crate delete <name>` | Deletes a crate | `dreamcrates.admin.delete` |
| `/crate givekey <player> <crate> [amount] [type]` | Gives keys to a player | `dreamcrates.admin.givekey` |
| `/crate reload` | Reloads the plugin configuration | `dreamcrates.admin.reload` |
| `/crate setlocation <crate>` | Sets the location of a crate | `dreamcrates.admin.setlocation` |
| `/crate preview <crate>` | Previews crate rewards | `dreamcrates.preview` |

## Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `dreamcrates.command` | Allows use of the /crate command | true |
| `dreamcrates.preview` | Allows previewing crate rewards | true |
| `dreamcrates.admin.create` | Allows creating crates | op |
| `dreamcrates.admin.delete` | Allows deleting crates | op |
| `dreamcrates.admin.givekey` | Allows giving keys to players | op |
| `dreamcrates.admin.reload` | Allows reloading the plugin | op |
| `dreamcrates.admin.setlocation` | Allows setting crate locations | op |
| `dreamcrates.admin` | Grants all admin permissions | op |

## Configuration

DreamCrates uses three main configuration files:

### config.yml

Contains general settings for the plugin:

```yaml
# DreamCrates - Main Configuration
settings:
  debug: false
  language: "en_US"
  use-holograms: true
  check-for-updates: true

holograms:
  enabled: true
  height: 1.5
  line-spacing: 0.25

messages:
  prefix: "&8[&bDreamCrates&8] "
  no-permission: "&cYou don't have permission to do that!"
  crate-created: "&aCrate '%name%' created successfully!"

animations:
  spin:
    duration: 80
    sound: "BLOCK_NOTE_BLOCK_PLING"
    sound-volume: 0.5
    sound-pitch: 1.0

daily-login-bonus:
  enabled: true
  crate: "daily"
  key-type: "VIRTUAL"
  message: "&aYou received a daily login bonus key!"
```

### crates.yml

Defines all crate types and their rewards:

```yaml
crates:
  # Common Crate
  common:
    display-name: "&aCommon Crate"
    gui-size: 27
    animation: "SPIN"
    key-type: "PHYSICAL"
    key-material: "TRIPWIRE_HOOK"
    hologram-color: "&a" # Green for common
    sounds:
      - "ENTITY_PLAYER_LEVELUP"
      - "ENTITY_FIREWORK_ROCKET_BLAST"
    particles:
      - "END_ROD"
      - "WITCH"
    rewards:
      iron_ingot:
        material: "IRON_INGOT"
        amount: 8
        display-name: "&fIron Ingot"
        lore:
          - "&7A common metal."
          - "&7From Common Crate"
        rarity: "COMMON"
        weight: 10.0
        commands:
          - "eco give {player} 50"
          - "tell {player} You received 50 coins with your iron ingots!"
```

### locations.yml

Stores the physical locations of placed crates (automatically generated).

## Crate Interaction

- **Left-Click** on a crate to preview its rewards
- **Right-Click** with the correct key to open the crate
- Virtual keys are automatically consumed when right-clicking a crate

## Animation Types

DreamCrates offers 5 unique animation types:

1. **SPIN**: Items rotate around the GUI border
2. **FLICKER**: Item appears and disappears in the center
3. **DROP**: Item drops from the top to bottom of GUI
4. **WHEEL**: A wheel of items rotates with an indicator
5. **CSGO**: Items scroll horizontally like CS:GO cases

## Creating a Crate

1. Use `/crate create <name>` to create a new crate
2. Edit `crates.yml` to configure the crate appearance and rewards
3. Use `/crate reload` to apply your changes
4. Use `/crate setlocation <name>` while looking at a block to place the crate

## Key Types

DreamCrates supports two types of keys:

1. **PHYSICAL**: Item-based keys that appear in player inventories
2. **VIRTUAL**: Virtual keys stored in the database, not in inventory

## Reward System

Rewards have several properties:

- **Material**: The Minecraft item to give
- **Amount**: How many of the item to give
- **Display Name**: Custom name for the item
- **Lore**: Custom lore for the item
- **Rarity**: COMMON, UNCOMMON, RARE, EPIC, LEGENDARY
- **Weight**: The chance of getting this reward (higher = more likely)
- **Commands**: Commands to execute when the reward is given
- **Command-only**: Set to true for rewards that only execute commands

## Placeholders in Commands

These placeholders can be used in reward commands:

- `{player}` - Player's name
- `{player_uuid}` - Player's UUID
- `{world}` - World name
- `{crate}` - Crate name
- `{reward}` - Reward ID

## Support

For support, please create an issue on the [GitHub repository](https://github.com/yourusername/DreamCrates/issues).

## License

This project is licensed under the MIT License - see the LICENSE file for details.
