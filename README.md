# ModernX
A fork of mpvX (based on [mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern/)), that aims to mirror the functionality of MPV's stock OSC while with a more modern-looking interface.

![image](preview.png)

# mpvconfig

This script is included in my [mpvconfig](https://github.com/zydezu/mpvconfig). Check that repository for a full mpv configuration.


# Additional Features
This fork changes the following:
- Adds compact mode and reorganises some features
- Added loop and pin window buttons
- Adds a download button for web videos
- Displays descriptions from web videos
- Made elements being unavailable vs being turned off (audio tracks and subtitles) more distinguishable
- Added shift+left clicking and shift+right clicking the audio/subtitles button for a list of tracks are shown and traversed through
- Pressing TAB shows a list of chapters
- Added dynamic title changing depending on the file/source being played
- Changed icon visibility range to prevent them from overlapping
- Many more configurable options
- Various bug fixes

# Installation

Locate your MPV folder. It is typically located at `\%APPDATA%\mpv\` on Windows and `~/.config/mpv/` on Linux/MacOS. See the [Files section](https://mpv.io/manual/master/#files) in mpv's manual for more info.

Place `modernx.lua` into your mpv `scripts/` folder. Create the `scripts/` folder if you don't already have one and remove any other OSC scripts.

Then place the two fonts in the `fonts/` folder. `Material-Design-Iconic-Font.ttf` can be downloaded [Material-Design-Iconic-Font.ttf](Material-Design-Iconic-Font.ttf) and `Material-Design-Iconic-Round.ttf` also [Material-Design-Iconic-Round.ttf](Material-Design-Iconic-Round.ttf).


### mpv.conf
Add the following lines to your `mpv.conf` file.
```
osc = no
border = no # Optional, but recommended
```


### Border differences

This is what disabling and enabling the border looks like:

| Border Enabled | Border Disabled |
| -------------- | --------------- |
| ![mpv_tkhXHUKNNt](https://github.com/zydezu/ModernX/assets/50119098/d2c3eb4e-5c7d-45df-ab35-6a0903c9c075) | ![mpv_rrIXTdX0Sx](https://github.com/zydezu/ModernX/assets/50119098/5573c30b-d57e-434a-b189-71dfb94b70bb) |

This option may vary depending on your system.


# Configuration

Create an `osc.conf` file and place it in the `script-opts/` folder (create the folder if you haven't already). A plethora options can be changed, so refer to the table of configurable `user_opts` parameters below for details.


### Example

Here is an example of a configuration file, in `script-opts/osc.conf`:

```
compactmode=no
showloop=no
showinfo=yes
titlefontsize=20
```

### Configurable Options

| Option   | Description |
| -- General Settings -- | --------------- |
| language | The language of the osc, mostly messages that are shown in the top left of the screen <br> ![mpv_2W4iPpqSKy](https://github.com/zydezu/ModernX/assets/50119098/19e517a5-4123-4d78-8113-b66a419b6e8d)|
| welcomescreen  | Whether to show the mpv 'Drop files or URLs to play here.' screen |
| visibility | The visiblity mode of the UI |
| windowcontrols | Whether to show window controls |
| showwindowed | Whether to show the OSC when windowed |
| showfullscreen | Whether to show the OSC when in fullscreen |
| noxmas | Disable showing the santa hat in December |
| -- Scaling Settings -- | --------------- |
| vidscale | Whether the OSC scales with the window's size |
| scalewindowed  | The scaling of the OSC when windowed |
| scalefullscreen | The scaling of the OSC when in fullscreen |
| scaleforcedwindow | The scaling when rendered on a forced window (like an audio file) |
| -- Interface Settings -- | --------------- |
| hidetimeout | Duration in ms until the OSC hides when there is no mouse movement |
| fadeduration | Duration in ms of the fade effect the OSC exihibts |
| minmousemove | The minimum amount of pixels the mouse has to move for the OSC to show |
| showonpause | Whether to disable the hide timeout on pause (when enabled, pausing will show the OSC instantly) |
| bottomhover | If the osc should only display when hovering over UI elements at the bottom of the window (includes the window control buttons) <br> ### **On:** <br> ![mpv_UuIaS6QEQG](https://github.com/zydezu/ModernX/assets/50119098/e1b81c25-7e14-42f0-9a8e-0626796e78cb) <br> **Off:** <br> ![mpv_PDZfBO3tVn](https://github.com/zydezu/ModernX/assets/50119098/2da844c8-e7d3-4ecc-9baf-dba5e421ab18) |
| raisesubswithosc | Whether to raise any subtitles being shown, if the OSC is being shown <br> ![mpv_gpAsmbHnNs](https://github.com/zydezu/ModernX/assets/50119098/1268597a-f6e8-415e-8e58-a9f5fd55c2be) |
| thumbnailborder | The width of outline of the [thumbnail border](thumbnails) |
| -- Title and Chapter Settings -- | --------------- |
| showtitle | Whether to show the title in the OSC |
| showdescription | Whether to show video description on web videos |
| showwindowtitle | Whether to show to window title, when the window is borderless/fullscreened (this will match whatever is set in your `mpv.conf` file) <br> ![mpv_4hhWPnDWZS](https://github.com/zydezu/ModernX/assets/50119098/59dff364-b5d5-4adb-bb43-fd323b8f1616) |
| dynamictitle | Changed what title information is shown depending on if the `filename` and `media-title` properties differ, seen most in audio files and playing urls |
| font | The font of the OSC, by default matches the font set in `mpv.conf` |
| title | What title is shown in the OSC, see the [mpv manual](https://mpv.io/manual/master/#command-interface-media-title) for more properties |
| titlefontsize | The size of the title text |
| chapter_fmt | The format of the chapter text when hovering over the seekbar. Use 'no' to disable |
| osc_color | The colour of the OSC and title bar
| blur_intensity | The strenght of the blur on the OSC
| boxalpha | Alpha of the fade box effect, 0 (opaque) to 255 (fully transparent) |
| -- Seekbar Settings -- | --------------- |
| seekbarfg_color | Colour of current seekbar progress and the handle
| seekbarbg_color | Colour of the remaining seekbar
| seekbarkeyframes | Whether to use keyframes when dragging the seekbar |
| seekbarhandlesize | How big the seek bar handle appears, from 0 to 1 |
| seekrange | Whether to show the buffer range on the seekbar |
| seekrangealpha | The transparency of seekranges |
| iconstyle | Whether the icons are normal or round varients - thanks to [https://github.com/cyl0/ModernX/pull/55](https://github.com/cyl0/ModernX/pull/55) |
| hovereffect | Whether buttons emit a glowing effect when hovered over
| -- Button Settings -- | --------------- |
| timetotal | Whether to display the total time instead of remaining time |
| timems | Whether to display time in milliseconds |
| jumpamount | How many seconds the jump buttons jump by |
| jumpiconnumber | Whether to show 5, 10 or 30 in the jump icons if the `jumpamount` are any of those values |
| jumpmode | What kind of seeking mode is used for the jump buttons |
| volumecontrol | Whether to show the mute button and volume slider |
| volumecontroltype | Whether to use linear or logarithmic volume scale |
| showjump | Whether to show the jump forward/backward buttons |
| showskip | Whether to show the chapter buttons |
| compactmode | Remove the 'jump' buttons and embed that functionality in the 'chapter' buttons, see [compact mode](https://github.com/zydezu/ModernX#compact-mode) for more information |
| showloop | Whether to show the loop button |
| loopinpause | Whether to activate looping by right clicking pause |
| showontop | Whether to show the pin window on top button |
| showinfo | Whether to show the info button |
| downloadbutton | Whether to show download button for web videos |

### Compact Mode

Compact mode is a setting you can enable in the configuration, it removes the skip buttons, and places that functionality within the chapter buttons, allowing for more space in the interface. Clicking the buttons will act as jumping, and shift clicking will act as skipping a chapter

| Compact Mode Enabled | Compact Mode Disabled |
| -------------- | --------------- |
| ![mpv_EIgoJwS7WX](https://user-images.githubusercontent.com/50119098/236636371-99c17ce7-443c-466e-a442-47bc3a6db573.png) | ![mpv_au7Au4oZso](https://user-images.githubusercontent.com/50119098/236636421-c247d9af-d982-4aba-9171-a4f8103eec16.png) |

This changes the actions of the playlist back/forward buttons in the following way:

* `Left mouse button` jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
* `Right mouse button` jumps forwards/backwards by 1 minute
* `Shift + Left mouse button` play previous/next file and show playlist
* `Shift + Right mouse button` show playlist

Please note that this option will override the `showjump` option.

### Thumbnails

To enable thumbnails in timeline, install [thumbfast](https://github.com/po5/thumbfast). No other step necessary.

![mpv_UzSC2z3vIt](https://user-images.githubusercontent.com/50119098/236636833-8bd0a665-7230-496f-89e8-0209de59c530.png)



# Buttons

Like the built-in script, some buttons may accept multiple mouse actions, here is a list:

_Note: Middle clicking performs the same function as Shift + Left Clicking, allowing for one handed use._

### Seekbar
* `Left mouse button` seek to chosen position
* `Right mouse button` seek to the head of chosen chapter
### Title
* `Left mouse button` show the full media title
* `Right mouse button` show the full filename
### Description (only on web videos)
* `Left mouse button` show the full description
### Playback time
* `Left mouse button` display time in milliseconds
### Duration
* `Left mouse button` display total time instead of remaining time
### Playlist back/forward buttons
* `Left mouse button` play previous/next file
* `Right mouse button` show playlist
* `Shift + Left mouse button` play previous/next file and show playlist
* `Shift + Right mouse button` show playlist
### Skip back/forward buttons
* `Left mouse button` go to previous/next chapter
* `Right mouse button` show chapter list
* `Shift + Left mouse button` go to previous/next chapter and show playlist
* `Shift + Right mouse button` show chapter list
* `TAB` show chapter list
### Jump back/forward buttons
* `Left mouse button` jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
* `Right mouse button` jumps forwards/backwards by 1 minute
* `Shift + Left mouse button` skips to the previous/next frame
### Audio/subtitle track buttons
* `Left mouse button/Right mouse button` cycle to next/previous track
* `Shift + Left mouse button` cycle to next/previous track and show track list
* `Shift + Right mouse button` show track list
### Pin button
* `Left mouse button` toggle pinning (and removing video border)
* `Right mouse button` toggle pinning without changing the border
### Volume
* `Left mouse button` mute/unmute video
* `Scroll wheel` change volume
