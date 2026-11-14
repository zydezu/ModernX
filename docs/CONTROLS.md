# ModernX Controls Guide

<img width="1717" height="108" alt="modernx-buttons" src="https://github.com/user-attachments/assets/8b310e93-eefe-4362-a5d1-993fb5d42fb3" />

## Optional keyboard pack (ModernX)

ModernX defaults to the ModernX key pack (`key_bindings=yes`). To disable it, add to `script-opts/modernx.conf`:

```ini
key_bindings=no
```

With `key_bindings=yes`, **mute is on `Ctrl+m`** (plain `m` opens the interactive menu; requires mpv ≥ 0.38 and the uosc **select** scripts). Other bindings include `MENU` / `Ctrl+p` (menu), `p` (pin / PiP), chapter keys (`Shift+←/→`, `Tab`), track keys (`z`/`c` cycle, `Z`/`C` select), playlist (`Ctrl+←/→`, `Ctrl+s` shuffle), `b` toggles persistent progress when that option is on, `d` opens the scrolling description when `show_description` is on, and **`DEL`** toggles theatre mode (OSC visibility `auto` ↔ `never`).

Theatre is also always available without the pack via `script-binding modernx/theatre` (or bind it yourself in `input.conf`).

## Layouts

Set `layout` in `modernx.conf` to `default`, `compact`, `mini`, `seekbar`, `original`, or `reduced`.

`original` and `reduced` use the ModernX control arrangement: title above the seekbar, transport buttons centered, side buttons at the edges. Current and total time are one combined time-codes control. `reduced` uses a shorter title, insets the seekbar next to that time display, and puts the chapter title at the top right. With `show_description=yes` (the default), `original` shows a description line when the file has metadata, a file size, or is a URL. Click that line, or press `d` when `key_bindings=yes`, to open the scrolling view. Links inside it can be cycled with Tab and opened with Enter. An unknown `layout` value is logged and the OSC uses `default`. Image files keep the image viewer layout.

## Button Interactions

Below is a list that explains the OSC buttons function depending on how you interact with them.

> [!NOTE]
> Middle clicking performs the same function as `Shift+left mouse button`, allowing for one handed use

### Title

| Action            | Function                     |
| ----------------- | ---------------------------- |
| Left mouse click  | Show current track details   |
| Right mouse click | Show menu with watch history |

### Seekbar

| Action                 | Function                           |
| ---------------------- | ---------------------------------- |
| Left mouse click       | Seek to position (using keyframes) |
| Middle mouse click     | Seek to the exact position         |
| Shift+left mouse click | Seek to the exact position         |
| Right mouse click      | Seek to the head of chosen chapter |
| Scroll wheel           | Seek forward/backwards             |

### Time Codes

| Action            | Function                                       |
| ----------------- | ---------------------------------------------- |
| Left mouse click  | Display remaining time instead of current time |
| Right mouse click | Display time in milliseconds                   |

### Play/Pause

| Action                 | Function                            |
| ---------------------- | ----------------------------------- |
| Left mouse click       | Toggle play/pause                   |
| Right mouse click      | Toggle enable/disable file loop     |
| Middle mouse click     | Toggle enable/disable playlist loop |
| Shift+left mouse click | Toggle enable/disable playlist loop |

### Track Back/Forward

| Action                 | Function                |
| ---------------------- | ----------------------- |
| Left mouse click       | Play previous/next file |
| Right mouse click      | Show a playlist menu    |
| Shift+left mouse click | Show a simple playlist  |
| Middle mouse click     | Show a simple playlist  |

### Skip Chapter Back/Forward

| Action                  | Function                              |
| ----------------------- | ------------------------------------- |
| Left mouse click        | Go to previous/next chapter           |
| Right mouse click       | Show an interactive chapters list     |
| Shift+left mouse click  | Show a simple chapters list           |

### Jump Back/Forward

| Action                 | Function                                                                |
| ---------------------- | ----------------------------------------------------------------------- |
| Left mouse click       | Jumps forwards/backwards by 10 seconds (or by `user_opts` `jumpamount`) |
| Right mouse click      | Jumps forwards/backwards by 1 minute                                    |
| Shift+left mouse click | Skips to the previous/next frame (and pauses)                           |
| Middle mouse click     | Skips to the previous/next frame (and pauses)                           |

### Audio/Subtitle/Secondary Subtitle

| Action                 | Function                            |
| ---------------------- | ----------------------------------- |
| Left mouse click       | Show an interactive tracks list     |
| Right mouse click      | Cycle audio/subtitle track          |
| Shift+left mouse click | Cycle audio/subtitle track down     |
| Scroll wheel           | Cycle audio/subtitle tracks up/down |

### Playlist

| Action            | Function                     |
| ----------------- | ---------------------------- |
| Left mouse click  | Show an interactive playlist |
| Right mouse click | Show an interactive menu     |

### Volume

| Action            | Function                      |
| ----------------- | ----------------------------- |
| Left mouse click  | Toggle mute on/off            |
| Right mouse click | Show audio device select menu |
| Scroll wheel      | Change volume up/down         |

### Statistics

| Action            | Function                           |
| ----------------- | ---------------------------------- |
| Left mouse click  | Display statistics of current file |

### Screenshot

| Action           | Function          |
| ---------------- | ----------------- |
| Left mouse click | Take a screenshot |

### Pin

| Action            | Function                                                      |
| ----------------- | ------------------------------------------------------------- |
| Left mouse click  | Toggle [`ontop`](https://mpv.io/manual/master/#options-ontop) |

### Loop

| Action             | Function                        |
| ------------------ | ------------------------------- |
| Left mouse click   | Toggle current file loop on/off |
| Right mouse click  | Toggle playlist loop on/off     |

### Shuffle

| Action            | Function                       |
| ----------------- | ------------------------------ |
| Left mouse click  | Toggle playlist shuffle on/off |

### Speed

| Action                 | Function                                  |
| ---------------------- | ----------------------------------------- |
| Left mouse click       | Increase playing speed by increments of 1 |
| Right mouse click      | Reset playing speed to normal             |
| Scroll wheel           | Inc/decrease playing speed by 0.25        |

### Download

| Action            | Function                             |
| ----------------- | ------------------------------------ |
| Left mouse click  | Download the current video/image URL |

### Cache

| Action            | Function                                  |
| ----------------- | ----------------------------------------- |
| Left mouse click  | Display cache information of current file |
