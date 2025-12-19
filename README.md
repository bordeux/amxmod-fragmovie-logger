# Fragmovie Logger

An AMX Mod X plugin for Counter-Strike 1.6 that automatically logs impressive gameplay moments to help you create fragmovies from your HLTV demos.

## Features

The plugin tracks and logs the following fragmovie-worthy moments:

- **Multi-kills** - 3+ kills within a configurable time window (triple, quadra, penta kills)
- **ACE** - Player kills entire enemy team (minimum 4 opponents)
- **Long-distance headshots** - Headshot kills from far distances
- **No-scope kills** - AWP/Scout kills without scoping
- **Jumpshot kills** - Kills while jumping/in the air
- **Knife kills** - All knife eliminations
- **Grenade kills** - HE grenade eliminations

## Installation

1. Download `fragmovie_logger.sma`
2. Compile the plugin using AMX Mod X compiler
3. Place the compiled `fragmovie_logger.amxx` file in `addons/amxmodx/plugins/`
4. Add `fragmovie_logger.amxx` to `addons/amxmodx/configs/plugins.ini`
5. Restart your server or change map

## Output

All logged events are saved to:
```
addons/amxmodx/logs/fragmovie_moments.log
```

### Log Format

Each entry includes:
- Timestamp (Date and Time)
- Map name
- Event type
- Player name(s)
- Additional details (distance, time span, etc.)

### Example Log Entries

```
[2025-12-19 15:30:45] [de_dust2] [TRIPLE KILL] PlayerName - 3 kills in 4.2 seconds
[2025-12-19 15:31:12] [de_dust2] [LONG DISTANCE HS] PlayerName killed EnemyName with awp from 2500 units
[2025-12-19 15:32:03] [de_dust2] [NO-SCOPE] PlayerName killed EnemyName with awp
[2025-12-19 15:33:25] [de_dust2] [JUMPSHOT HEADSHOT] PlayerName killed EnemyName with ak47
[2025-12-19 15:34:20] [de_dust2] [ACE] PlayerName - killed entire enemy team (5 players)
[2025-12-19 15:35:10] [de_dust2] [KNIFE KILL] PlayerName killed EnemyName with knife
```

## Configuration (CVars)

Add these to your `server.cfg` or `amxmodx.cfg` to customize the plugin:

### Multi-kill Settings
```
fml_multikill_count 3      // Minimum kills required for multi-kill logging (default: 3)
fml_multikill_time 5.0     // Time window in seconds for multi-kills (default: 5.0)
```

### Long Distance Headshot Settings
```
fml_longdist_enable 1      // Enable long distance headshot logging (default: 1)
fml_min_distance 2000.0    // Minimum distance in units for impressive headshot (default: 2000.0)
```

### ACE Settings
```
fml_log_ace 1              // Enable ACE logging (default: 1)
fml_min_enemy_team 4       // Minimum enemy team size for ACE (default: 4)
```

### Feature Toggles
```
fml_log_grenade 1          // Log grenade kills (default: 1)
fml_log_knife 1            // Log knife kills (default: 1)
fml_log_noscope 1          // Log AWP/Scout no-scope kills (default: 1)
fml_log_jumpshot 1         // Log kills while jumping (default: 1)
```

## Usage with HLTV Demos

1. Run your server with HLTV recording enabled
2. Play normally - the plugin will automatically log impressive moments
3. After gameplay, check `fragmovie_moments.log` for timestamps
4. Open the corresponding HLTV demo and navigate to the timestamps
5. Record the moments for your fragmovie

### Tips

- The timestamp in the log corresponds to real time, not demo time
- Note the map name to ensure you're checking the correct demo
- Use the player names to help locate the exact moment in the demo
- For multi-kills, the timestamp shows when the sequence started

## In-Game Notifications

Players will see chat notifications for certain events:
- Multi-kills (triple, quadra, penta)
- Long-distance headshots (with distance)
- No-scope kills
- Jumpshot kills
- ACE achievements

Example:
```
[FragMovie] PlayerName: TRIPLE KILL in 4.2 seconds!
[FragMovie] PlayerName: Long distance headshot! (2500 units)
[FragMovie] PlayerName: JUMPSHOT HEADSHOT!
[FragMovie] PlayerName: ACE - killed entire enemy team (5 players)!
```

## Requirements

- AMX Mod X 1.8.2 or higher
- Counter-Strike 1.6
- Modules: fakemeta

## Version

Current version: 1.0

## Support

For issues or feature requests, please check the plugin source code or contact the server administrator.

## License

Free to use and modify for your Counter-Strike 1.6 servers.
