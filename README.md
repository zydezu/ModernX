# ModernX
A fork of mpvX (based on [mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern/)), that aims to mirror the functionality of MPV's stock OSC while with a more modern-looking interface.

![image](https://user-images.githubusercontent.com/50119098/232332600-afb7ba86-9bdb-4aca-8b98-386ed8ad872d.png)


# Additional Features
This fork changes the following:
- Added loop button, and option to disable it
- Added options to disable the info button, the skip buttons and the back/next buttons
- Moving the volume slider whilst muted now unmutes it
- When muted, the slider becomes 0 (but the volume of the video is remembered when unmuted)
- Although... scrolling up whilst volume is muted sets it to 0 and increases it from there
- Unmuting whilst the volume slider is already 0 increases the volume from 0
- Made elements being unavailable vs being off (audio tracks and subtitles) more distinguishable
- When shift+left clicking the audio/subtitles button, a list of tracks are shown and traversed through
- When shift+right clicking the same button, the list is shown, but the track isn't changed
- This shift-clicking rule also applies for the skip buttons and back/next buttons
- Full keyboard control now shows messages when enter is pressed on the relevant icon (eg: showing the list of chapters when the skip forward is pressed)
- Changed icon window x visibility range to prevent them from overlapping
- Added Japanese translation
- N/A when hovering over audio will not show if either the audio track's language or title are known
- Added ability to hide pin window button


# Installation

Locate your MPV folder. It is typically located at `\%APPDATA%\mpv\` on Windows and `~/.config/mpv/` on Linux/MacOS. See the [Files section](https://mpv.io/manual/master/#files) in mpv's manual for more info.

Place `modernx.lua` into your mpv `scripts/` folder. Create the `scripts/` folder if you don't already have one and remove any other OSC scripts.

Then place `Material-Design-Iconic-Font.ttf` in the `fonts/` folder. `Material-Design-Iconic-Font.ttf` can be downloaded [here](https://zavoloklom.github.io/material-design-iconic-font/).


### mpv.conf
Add the following lines to your `mpv.conf` file.
```
osc = no
border = no # Optional, but recommended
```


### Border differences

This is what disabling and enablign the border looks like:

| Border Enabled | Border Disabled |
| -------------- | --------------- |
| ![mpv_1XwH1nkvPx](https://user-images.githubusercontent.com/50119098/236631985-8f21b44e-9ac2-410f-8235-2e2d7663022e.png) | ![mpv_oMMAipwaUu](https://user-images.githubusercontent.com/50119098/236632168-fd3687d4-dee1-4569-ba5b-759a4ae776ff.png) 

This option may vary depending on your system.


# Configuration

Create an `osc.conf` file and place it in the `script-opts/` folder (create the folder if you haven't already). A plethora options can be changed, so refer to the table of configurable `user_opts` parameters below for details.


### Example

Here is an example of a configuration file, in `script-opts/osc.conf`:

```
showloop=no
showinfo=no
titlefontsize=20
```

### Configurable Options

| Option   | Description |
| -------------- | --------------- |
| language | The language of the osc, mostly messages that are shown in the top left of the screen <br> ![mpv_ddz7rfBxHy](https://user-images.githubusercontent.com/50119098/236633617-baeec145-9ce2-4246-9c6d-f7ecc651aa71.png) |
| showwindowed   | Whether to show the OSC when windowed |
| showfullscreen | Whether to show the OSC when in fullscreen |
| welcomescreen  | Whether to show the mpv 'Drop files or URLs to play here.' screen |
| scalewindowed  | The scaling of the OSC when windowed |
| scalefullscreen | The scaling of the OSC when in fullscreen |
| scaleforcedwindow | The scaling when rendered on a forced window (like an audio file) |
| titlefontsize | The size of the title text |
| titlecutoff | Whether the title text is cut of and '...' appended to it, if it is too long <br> ![mpv_S3vkkf8YrJ](https://user-images.githubusercontent.com/50119098/236633686-40b99da5-dede-48f1-b937-02bcbf54bec8.png) 
| scrollingtitle | Whether the the title text scrolls when too long (overrides 'titlecutoff') <br> ![mpv_5ez7Us4X9A](https://user-images.githubusercontent.com/50119098/236633730-e28a60b5-27c7-444f-9da5-27f6348b9f6e.gif) |
| vidscale | Whether the OSC scales with the window's size |
| hidetimeout | Duration in ms until the OSC hides when there is no mouse movement |
| fadeduration | Duration in ms of the fade effect the OSC exihibts |
| minmousemove | The minimum amount of pixels the mouse has to move for the OSC to show |
| minmousemove | The minimum amount of pixels the mouse has to move for the OSC to show |
| font | The font of the OSC, by default matches the font set in `mpv.conf` |
| seekbarhandlesize | How big the seek bar handle appears, from 0 to 1 |
| seekrange | Whether to show the buffer range on the seekbar |
| seekrangealpha | The transparency of seekranges |
| seekbarkeyframes | Whether to use keyframes when dragging the seekbar |
| showjump | Whether to show the jump forward/backward buttons |
| showskip | Whether to show the chapter buttons |
| showloop | Whether to show the loop button |
| showinfo | Whether to show the info button |
| showontop | Whether to show the pin window on top button |
| volumecontrol | Whether to show the mute button and volume slider |
| compactmode | Remove the 'jump' buttons and embed that functionality in the 'chapter' buttons, see [compact mode](compact-mode) for more information |
| bottomhover | If the osc should only display when hovering over UI elements at the bottom of the window (includes the window control buttons) |
| jumpamount | How many seconds the jump buttons jump by |
| jumpiconnumber | Whether to show 5, 10 or 30 in the jump icons if the `jumpamount` are any of those values |
| jumpmode | What kind of seeking mode is used for the jump buttons |
| title | What title is shown in the OSC, see the [mpv manual](https://mpv.io/manual/master/#command-interface-media-title) for more properties |
| showtitle | Whether to show the title in the OSC |
| showwindowtitle | Whether to show to window title, when the window is borderless/fullscreened (this will match whatever is set in your `mpv.conf` file) <br> ![mpv_jrEP1mKJ2A](https://user-images.githubusercontent.com/50119098/236635427-7c78b93e-d37c-48c6-9209-e10ffabdcab5.png) |
| showonpause | Whether to disable the hide timeout on pause (when enabled, pausing will show the OSC instantly) |
| thumbnailborder | The width of outline of the [thumbnail border](thumbnails) |
| raisesubswithosc | Whether to raise any subtitles being shown, if the OSC is being shown <br> ![mpv_iRUTYp69ew](https://user-images.githubusercontent.com/50119098/236637089-361745a1-f9e0-46e2-970f-d11a58ce8685.gif)
 |
| timetotal | Whether to display the total time instead of remaining time |
| timems | Whether to display time in milliseconds |
| visibility | only used at init to set visibility_mode(...) |
| windowcontrols | Whether to show window controls |
| greenandgrumpy | Disable showing the santa hat in December |
| keyboardnavigation | Enable full keyboard control of the OSC |
| chapter_fmt | The format of the chapter text when hovering over the seekbar. Use 'no' to disable |
| boxalpha | Alpha of the fade box effect, 0 (opaque) to 255 (fully transparent) |


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
### Playback time
* `Left mouse button` display time in milliseconds
### Duration
* `Left mouse button` display total time instead of remaining time
