# PlayerTabHider

Hide the players you list from the tab list and from the player count of the server, straight from a configuration file, with nothing to install on the client.

## Features

- The players named in the configuration disappear from the tab list as soon as somebody connects.
- They are hidden from the server list ping as well: they are removed from the player sample and the online player count is lowered, so the multiplayer screen shows the same numbers as the game itself.
- Server side only: it is a Fabric mod built on mixins, so a vanilla client sees the result without installing anything.
- Nothing is hardcoded: the list of hidden names and the on/off switch live in `config/playertabhider.json`.

## Requirements

- A Minecraft 1.18.x **server** running Fabric Loader 0.11.3 or newer, on Java 17.
- [Fiber](https://github.com/FabLabsMC/fiber), the configuration library: it is bundled into the built jar, so it does not have to be installed next to the mod.

## Installation

1. Build the mod (see below) and drop the jar in the `mods/` folder of your Fabric server.
2. Start the server once: `config/playertabhider.json` is created.
3. Add the names to hide to that file and restart the server.

## Configuration

```json
{
  "hide_players": {
    "enabled": true,
    "value": ["Bot"]
  }
}
```

- `enabled`: whether the players are hidden at all.
- `value`: the names of the players to hide.

The file is read when the server starts, and rewritten with the defaults when it is missing or unreadable.

## Building

```sh
./gradlew build
```

The mod lands in `build/libs/`. It is built against Minecraft 1.18.1, and the versions it uses are the ones in `gradle.properties`.
