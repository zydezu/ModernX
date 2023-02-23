# ModernX
A fork of mpvX (based on [mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern/)), that aims to mirror the functionality of MPV's stock OSC while with a more modern-looking interface.

![img](https://github.com/cyl0/ModernX/blob/main/preview.png)

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

# How to install

Locate your MPV folder. It is typically located at `\%APPDATA%\mpv\` on Windows and `~/.config/mpv/` on Linux/MacOS. See the [Files section](https://mpv.io/manual/master/#files) in mpv's manual for more info.

Put mordenx.lua into your mpv "\~\~/scripts/" folder. Create the "\~\~/scripts/" folder if you don't already have one and remove any other OSC scripts,
then put `Material-Design-Iconic-Font.ttf` in the "\~\~/fonts" folder.

in mpv.conf:

```
osc = no
border = no # Optional, but recommended
```
`Material-Design-Iconic-Font.ttf` can also be downloaded from [here](https://zavoloklom.github.io/material-design-iconic-font/).

# How to config

edit osc.conf in "\~\~/script-opts/" folder, however many options are changed, so refer to the user_opts variable in the script file for details.

# Thumbnails

To enable thumbnails in timeline, install [thumbfast](https://github.com/po5/thumbfast). No other step necessary.

# Buttons

Like the built-in script, some buttons may accept multiple mouse actions, here is a list:

_Note: Middle clicking performs the same function as Shift + Left Clicking, allowing for one handed use._

## Seekbar
* Left mouse button: seek to chosen position
* Right mouse button: seek to the head of chosen chapter
## Playlist back/forward buttons
* Left mouse button: play previous/next file
* Right mouse button: show playlist
* Shift + Left mouse button: play previous/next file and show playlist
* Shift + Right mouse button: show playlist
## Skip back/forward buttons
* Left mouse button: go to previous/next chapter
* Right mouse button: show chapter list
* Shift + Left mouse button: go to previous/next chapter and show playlist
* Shift + Right mouse button: show chapter list
## Jump back/forward buttons
* Left mouse button: jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
* Right mouse button: jumps forwards/backwards by 1 minute
* Shift + Left mouse button: skips to the previous/next frame
## Audio/subtitle track buttons
* Left mouse button/Right mouse button: cycle to next/previous track
* Shift + Left mouse button: cycle to next/previous track and show track list
* Shift + Right mouse button: show track list
## Volume
* Left mouse button: mute/unmute video
* Scroll wheel: change volume
## Playback time
* Left mouse button: display time in milliseconds
## Duration
* Left mouse button: display total time instead of remaining time

# Compact Mode

Compact mode is a setting you can enable in the configuration, it removes the skip buttons, and places that functionality within the chapter buttons, allowing for more space in the interface. 

This changes the actions of the playlist back/forward buttons in the following way:

* Left mouse button: jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
* Right mouse button: jumps forwards/backwards by 1 minute
* Shift + Left mouse button: play previous/next file and show playlist
* Shift + Right mouse button: show playlist
