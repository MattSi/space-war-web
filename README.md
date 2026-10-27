# Space War

A 2D platform shooter made with **Godot 4.7**.

This repository only holds the web build. **Source code:** https://github.com/MattSi/space-war

## ▶ Play

**https://mattsi.github.io/space-war-web/**

Play it in Chrome or Edge on a computer. Click the game once to turn on sound. You need a keyboard or a gamepad.

<!-- Screenshot: add one here, e.g. ![Space War](screenshot.png) -->

## Controls

| Action | Keyboard | Gamepad |
|---|---|---|
| Move | `A` `D` or `←` `→` | Left stick |
| Jump / double jump | `Space` | `A` |
| Shoot | `J` | `RT` |
| Aim (hold) | `K` or `Shift` | `LT` |
| Aim direction | `W` `A` `S` `D` or arrow keys | Left stick |

Hold jump to jump higher. Hold aim to shoot in 16 directions.

## Game

- 2 levels. Reach the goal to finish a level.
- You have 5 health points.
- Touch a checkpoint to restart there when you die.

## Features

- Smooth jumping: double jump, jump height control, and a short grace time at ledges.
- Aiming in 16 directions.
- Checkpoints and a short invincibility time after a hit.

## How it's built

About 1,100 lines of GDScript.

**Structure**
- Each game object (player, enemy, bullet, checkpoint, goal) is its own small scene. Levels are made by placing these scenes.
- Two global managers:
  - `GameManager` loads levels and handles checkpoints and respawns.
  - `AudioManager` plays music and sounds by name.

**Patterns**
- **Signals (Observer):** the player sends events like `died` and `health_changed`. The HUD and `GameManager` react to them.
- **State machine:** enemies switch between states, e.g. `PATROL → CHASE → DIVE → DEAD`.
- **Shared `take_damage()`:** bullets can hit anything that has this method, so player and enemies use the same bullet.
- **Groups:** objects find the player through the `Player` group, not a fixed path.

**Small details**
- Checkpoints are kept after you die and the level reloads.
- Game values (speed, jump, health) are set in the Godot editor.
- Keyboard and gamepad use the same input actions.

## Credits

- **Music:** "Orbital Colossus" by **Matthew Pablo** (https://www.matthewpablo.com), [OpenGameArt](https://opengameart.org/content/space-boss-battle-theme), [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/).
<!-- TODO: credit the sprites and sound effects (author, link, license) -->

Made by **Mian Si** ([MattSi](https://github.com/MattSi)).
