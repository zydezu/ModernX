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

Put mordenx.lua into your mpv `scripts/` folder. Create the `scripts/` folder if you don't already have one and remove any other OSC scripts.

Then put `Material-Design-Iconic-Font.ttf` in the `fonts/` folder. `Material-Design-Iconic-Font.ttf` can be downloaded [here](https://zavoloklom.github.io/material-design-iconic-font/).


### mpv.conf:
Place the following lines into your `mpv.conf` file.
```
osc = no
border = no # Optional, but recommended
```


### Border differences

| Border Enabled | Border Disabled |
| -------------- | --------------- |
| ![mpv_1XwH1nkvPx](https://user-images.githubusercontent.com/50119098/236631985-8f21b44e-9ac2-410f-8235-2e2d7663022e.png) | ![mpv_oMMAipwaUu](https://user-images.githubusercontent.com/50119098/236632168-fd3687d4-dee1-4569-ba5b-759a4ae776ff.png) 

This option may vary depending on your system.


# Configuration

Create an `osc.conf` file in the `script-opts/` folder (create this if you don't have one already). Many options can be changed, so refer to the table of `user_opts` contents below for details.


### Example

Here is an example of a configuration file, in `script-opts/osc.conf`:

```
showloop=no
showinfo=no
titlefontsize=20
```

### Parameters and what they do

| language | The language of the osc, mostly messages that are shown in the top left of the screen <br> ![mpv_ddz7rfBxHy](https://user-images.githubusercontent.com/50119098/236632634-ee759477-b33e-47c2-978d-ba51edc66c71.png) |
| -------------- | --------------- |
| showwindowed   | whether to show the OSC when windowed |
| -------------- | --------------- |
| showfullscreen | whether to show the OSC when in fullscreen |
| -------------- | --------------- |
| welcomescreen  | whether to show the mpv 'Drop files or URLs to play here.' screen |
| -------------- | --------------- |
| scalewindowed  | The scaling of the OSC when windowed |
| -------------- | --------------- |
| scalefullscreen | The scaling of the OSC when in fullscreen |
| -------------- | --------------- |
| scaleforcedwindow | The scaling when rendered on a forced window (like an audio file) |
| -------------- | --------------- |

### Compact Mode

![mpv_9n9ltyRJf6](https://user-images.githubusercontent.com/50119098/236631106-f360bad9-d8fc-4986-b419-15474094a339.png)


Compact mode is a setting you can enable in the configuration, it removes the skip buttons, and places that functionality within the chapter buttons, allowing for more space in the interface (as seen in the photo above).

This changes the actions of the playlist back/forward buttons in the following way:

* `Left mouse button` jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
* `Right mouse button` jumps forwards/backwards by 1 minute
* `Shift + Left mouse button` play previous/next file and show playlist
* `Shift + Right mouse button` show playlist

Please note that this option may override the following settings:
```
    showjump = true
```


### Thumbnails

To enable thumbnails in timeline, install [thumbfast](https://github.com/po5/thumbfast). No other step necessary.


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
