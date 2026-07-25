# ModernX
>
> [!IMPORTANT]
> This script is updated frequently at [mpvconfig](https://github.com/zydezu/mpvconfig), stable builds are released here in the [releases](https://github.com/zydezu/ModernX/releases) tab.

A fork of modernX (based on [mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern/)), that aims to mirror the functionality of MPV's stock OSC while with a more modern-looking interface.

<img src="https://github.com/zydezu/ModernX/blob/main/img/preview.png?raw=true">

> [!NOTE]
> This script is included in my [mpvconfig](https://github.com/zydezu/mpvconfig), check that repository for a full mpv configuration

## Additional Features

This fork changes the following:

- Adds compact mode and reorganises some features
- Added loop and pin window buttons
- Adds a download button for web videos
- Displays descriptions, likes and dislike counts from web videos
- Links found in video descriptions can be selected (`Tab`/`Shift+Tab`) and opened (`Enter`)
- Added shift+left clicking and shift+right clicking the audio/subtitles button for a list of tracks are shown and traversed through
- Pressing TAB shows a list of chapters
- Added dynamic title changing depending on the file/source being played
- Automatically resumes playback when navigating to a different playlist item while paused
- Many more configurable options
- Various bug fixes

## Installation

Locate your MPV folder. It is typically located at `\%APPDATA%\mpv\` on Windows and `~/.config/mpv/` on Linux/MacOS. See the [Files section](https://mpv.io/manual/master/#files) in mpv's manual for more info.

> [!NOTE]
> Create these folders if you don't have them already

Place `modernx.lua` into your mpv `scripts/` folder, remove any previous OSC scripts.

Then place the font in the `fonts/` folder. [fluent-system-icons.ttf](fluent-system-icons.ttf) (click the link to download).

### mpv.conf

Add the following lines to your `mpv.conf` file.

> [!NOTE]
> Please note that `.conf` files use yes/no in place of true/false

```editorconfig
osc=no
border=no #optional - if you don't want to see the OS border
```

## SponsorBlock

To allow SponsorBlock segments to show up on the timeline, please add this script to your mpv scripts directory. https://github.com/zydezu/mpvconfig/blob/main/scripts/sponsorblock.lua

![image](https://github.com/user-attachments/assets/a7dd23bb-f59e-4f0a-bbcb-b9c5c759e802)

## Configuration

Create an `modernx.conf` file and place it in the `script-opts/` folder (create the folder if you haven't already). A plethora of options can be changed, so please refer to the table of configurable `user_opts` parameters below for detailed explanations of settings.

### Example

Here is an example of a configuration file, which would be placed in `script-opts/modernx.conf`:

```editorconfig
compact_mode=no
info_button=yes
title_font_size=20
seek_handle_size=0
```

### Configurable Options

The default options are shown below:

```lua
-- Parameters
-- default user option values
-- change them using modernx.conf
local user_opts = {
    -- Language and display
    language = "en",            -- en:English - .json translations need implementing
    font = "mpv-osd-symbols",   -- font for the OSC (default: mpv-osd-symbols or the one set in mpv.conf)
    layout_option = "original", -- use the original/reduced layout
    idle_screen = true,         -- show mpv logo when idle
    key_bindings = true,        -- register additional key bindings, such as chapter scrubbing, pinning the window
    window_top_bar = "auto",    -- show OSC window top bar: "auto", "yes", or "no" (borderless/fullscreen)
    show_windowed = true,       -- show OSC when windowed
    show_fullscreen = true,     -- show OSC when fullscreen
    show_on_pause = true,       -- show OSC when paused
    keep_on_pause = false,      -- disable OSC hide timeout when paused
    green_and_grumpy = false,   -- disable the Santa hat in December
    visibility = "auto",        -- only used at init to set visibility_mode(...)

    -- OSC behaviour and scaling
    hide_timeout = 1500,             -- time (in ms) before OSC hides if no mouse movement
    seek_resets_hide_timeout = true, -- if seeking should reset the hide_timeout
    fade_duration = 150,             -- fade-out duration (in ms), set to 0 for no fade
    min_mouse_move = 0,              -- minimum mouse movement (in pixels) required to show OSC
    bottom_hover = true,             -- show OSC only when hovering at the bottom
    bottom_hover_zone = 175,         -- height of hover zone for bottom_hover (in pixels)
    osc_on_seek = false,             -- show OSC when seeking
    osc_keep_with_cursor = false,    -- keep OSC visible if mouse cursor is within OSC boundaries
    mouse_seek_pause = true,         -- pause video while seeking with mouse move (on button hold)

    vid_scale = false,               -- scale osc with the video
    scale_windowed = 1.0,            -- osc scale factor when windowed
    scale_fullscreen = 1.0,          -- osc scale factor when fullscreen
    scale_forced_window = 1.0,       -- osc scale factor when forced (no video, for example music files)

    -- Time, title and description display
    show_title = true,             -- show title in the OSC (above seekbar)
    title = "${media-title}",      -- title above seekbar format: "${media-title}" or "${filename}"
    title_font_size = 28,          -- font size of the title text (above seekbar)
    dynamic_title = true,          -- change title if {media-title} and {filename} differ (eg: when playing URLs or audio)

    show_chapter_title = true,     -- show chapter title alongside timestamp (below seekbar)
    chapter_fmt = "%s",            -- format for chapter display on seekbar hover (set to "no" to disable)
    chapter_hover_title = false,   -- show the hovered chapter's name in place of the main title while scrubbing (only applies when thumbfast isn't available)
    chapter_hover_subtitle = true, -- show the hovered chapter's name in the chapter title text below the seekbar instead of the main title (only applies when thumbfast isn't available)
    show_chapter_markers = true,   -- show chapter markers on the seekbar
    chapter_marker_style = "gap",  -- shape of chapter markers: "triangle", "bar", "single-bar", or "gap"
    show_top_mark = true,          -- show the top part of the chapter marker (only for the "triangle" chapter_marker_style)
    show_bottom_mark = false,      -- show the bottom part of the chapter marker (only for the "triangle" chapter_marker_style)

    time_total = true,             -- show total time instead of remaining time
    time_ms = false,               -- show timecodes with milliseconds
    unicode_minus = false,         -- use the Unicode minus sign in remaining time
    time_format = "dynamic",       -- "dynamic" or "fixed" - dynamic shows MM:SS when possible, fixed always shows HH:MM:SS
    time_font_size = 18,           -- font size of the time display

    show_description = true,       -- show video description - description on web videos or metadata/stats on local video
    show_file_size = true,         -- show the current file's size in the description
    description_font_size = 19,    -- font size of the description text (below title)
    description_alpha = 100,       -- alpha of the description background box
    scrolling_speed = 40,          -- the speed of scrolling text in description/comment menus

    date_format = "%Y-%m-%d",      -- how dates should be formatted, when read from metadata (uses standard lua date formatting)

    -- Title bar settings
    window_title = true,                      -- show window title in borderless/fullscreen mode
    window_controls = true,                   -- show window controls (close, minimize, maximize) in borderless/fullscreen
    window_controls_title = "${media-title}", -- same as title but for window_controls

    -- Subtitle display settings
    raise_subtitles = true,      -- whether to raise subtitles above the osc when it's shown
    raise_subtitle_amount = 160, -- how much subtitles rise when the osc is shown

    -- Buttons display and functionality
    compact_mode = true,            -- replace the jump buttons with the seek/chapter buttons

    jump_buttons = true,            -- show the jump backward and forward buttons
    jump_amount = 10,               -- change the jump amount in seconds
    jump_more_amount = 60,          -- change the jump amount in seconds when right-clicking jump buttons and shift-clicking chapter skip buttons
    jump_icon_number = true,        -- show different icon when jump_amount is set to 5, 10, or 30
    jump_mode = "relative",         -- seek mode for jump buttons
    jump_softrepeat = true,         -- enable continuous jumping when holding down seek buttons
    chapter_skip_buttons = true,    -- show the chapter skip backward and forward buttons
    chapter_softrepeat = false,     -- enable continuous skipping when holding down chapter skip buttons
    track_nextprev_buttons = true,  -- show next/previous playlist track buttons

    volume_control = true,          -- show mute button and volume slider
    volume_control_type = "linear", -- volume scale type: "linear" or "logarithmic"

    info_button = false,            -- show info button
    ontop_button = true,            -- show window on top button
    screenshot_button = false,      -- show screenshot button
    screenshot_flag = "subtitles",  -- flag for screenshot button: "subtitles", "video", "window", "each-frame"
    -- https://mpv.io/manual/master/#screenshot-commands

    download_button = true,            -- show download button on web videos (requires yt-dlp and ffmpeg)
    download_path = "~/Pictures/mpv/", -- default download directory for videos (https://mpv.io/manual/master/#paths)

    loop_button = false,               -- show loop button
    loop_in_pause = true,              -- enable looping by right-clicking pause

    playpause_size = 30,               -- icon size for the play/pause button
    midbuttons_size = 24,              -- icon size for the middle buttons
    sidebuttons_size = 24,             -- icon size for the side buttons

    -- Colors and style
    osc_color = "#000000",                    -- accent color of the OSC and title bar
    window_title_color = "#FFFFFF",           -- color of the title in borderless/fullscreen mode
    window_controls_color = "#FFFFFF",        -- color of the window controls (close, minimize, maximize) in borderless/fullscreen mode
    window_controls_close_hover = "#E81123",  -- color of close window control on hover
    window_controls_minmax_hover = "#53A4FC", -- color of min/max window controls on hover
    title_color = "#FFFFFF",                  -- color of the title (above seekbar)
    seekbarfg_color = "#1D96F5",              -- color of the seekbar progress and handle, in Hex color format
    seekbarbg_color = "#FFFFFF",              -- color of the remaining seekbar, in Hex color format
    seekbar_cache_color = "#1D96F5",          -- color of the cache ranges on the seekbar
    volumebar_match_seek_color = false,       -- match volume bar color with seekbar color (ignores side_buttons_color)
    time_color = "#FFFFFF",                   -- color of the timestamps (below seekbar)
    chapter_title_color = "#FFFFFF",          -- color of the chapter title next to timestamp (below seekbar)
    chapter_marker_color = "#1D96F5",         -- color of chapter markers on the seekbar
    chapter_marker_current_color = "#9D96f5", -- color of the marker for the current chapter
    side_buttons_color = "#FFFFFF",           -- color of the side buttons (audio, subtitles, playlist, etc.)
    middle_buttons_color = "#FFFFFF",         -- color of the middle buttons (skip, jump, chapter, etc.)
    playpause_color = "#FFFFFF",              -- color of the play/pause button
    held_element_color = "#999999",           -- color of the element when held down (pressed)
    hover_effect_color = "#FFFFFF",           -- color of a hovered button when hover_effect includes "color"
    thumbnail_border_color = "#FFFFFF",       -- color of the border for thumbnails (with thumbfast)
    thumbnail_border_outline = "#000000",     -- color of the border outline for thumbnails

    fade_alpha = 100,                         -- alpha of the title bar background box
    fade_blur_strength = 75,                  -- blur strength for the OSC alpha fade - caution: high values can take a lot of CPU time to render
    fade_transparency_strength = 0,           -- use with "fade_blur_strength = 0" to create a transparency box
    window_fade_alpha = 100,                  -- alpha of the window title bar
    window_fade_blur_strength = 75,           -- blur strength for the window title bar. caution: high values can take a lot of CPU time to render
    window_fade_transparency_strength = 0,    -- use with "window_fade_blur_strength = 0" to create a transparency box
    thumbnail_border = 1,                     -- width of the thumbnail border (for thumbfast)
    thumbnail_border_radius = 5,              -- rounded corner radius for thumbnail border (0 to disable)

    -- Button hover effects
    hover_effect = "size,glow,color", -- active button hover effects: "glow", "size", "color"; can use multiple separated by commas
    hover_button_size = 115,          -- relative size of a hovered button if "size" effect is active
    button_glow_amount = 5,           -- glow intensity when "glow" hover effect is active
    hover_effect_for_sliders = false, -- apply hover effects to slider handles

    -- Progress bar settings
    seek_handle_size = 0.8,              -- size ratio of the seekbar handle (range: 0 ~ 1)
    seekbar_between_timers = false,      -- moves the seekbar and progress bar between the timers
    seekbar_height = 2,                  -- height of the seekbar
    progress_bar_height = 16,            -- height of the progress bar
    seek_range = true,                   -- show seek range overlay
    seek_range_alpha = 175,              -- transparency of the seek range
    seekbar_keyframes = true,            -- use keyframes when dragging the seekbar

    automatic_keyframe_mode = true,      -- automatically set seekbar_keyframes for the seekbar based on video length defined in automatic_keyframe_limit
    automatic_keyframe_limit = 1800,     -- videos longer than this (in seconds) will have seekbar_keyframes set to true

    persistent_progress_default = false, -- always show a small progress line at the bottom of the screen
    persistent_progress_height = 17,     -- height of the persistent_progress bar
    persistent_buffer = false,           -- show the buffer on the persistent progress line
    persistent_progress_toggle = true,   -- enable toggling the persistent_progress bar

    -- Web videos
    title_youtube_stats = true, -- update the window/OSC title bar with YouTube video stats (views, comments, likes)
    ytdl_format = "",           -- optional parameteres for yt-dlp downloading, eg: '-f bestvideo+bestaudio/best'

    -- SponsorBlock - these SponsorBlock features need https://github.com/zydezu/mpvconfig/blob/main/scripts/sponsorblock.lua specifically to function
    show_sponsorblock_segments = true,             -- show SponsorBlock segments on the progress bar
    add_sponsorblock_chapters = false,             -- add SponsorBlock chapters to the chapter list
    sponsorblock_seek_range_alpha = 75,            -- transparency of SponsorBlock segments
    sponsor_types = {                              -- what categories to show in the progress bar
        "sponsor",                                 -- all categories: sponsor, intro, outro,
        "intro",                                   -- interaction, selfpromo, preview, music_offtopic, filler
        "outro",                                   -- video outro
        "interaction",                             -- interaction reminders such as liking and subscribing
        "selfpromo",                               -- self promotion of socials or other channels
        "preview",                                 -- video preview
        "music_offtopic",                          -- silence in music videos
        "filler"                                   -- filler content/tangents
    },
    sponsorblock_sponsor_color = "#00D400",        -- color for sponsors
    sponsorblock_intro_color = "#00FFFF",          -- color for intermission/intro animations
    sponsorblock_outro_color = "#0202ED",          -- color for endcards/credits
    sponsorblock_interaction_color = "#CC00FF",    -- color for interaction reminders (reminders to subscribe)
    sponsorblock_selfpromo_color = "#FFFF00",      -- color for unpaid/self promotion
    sponsorblock_preview_color = "#008FD6",        -- color for unpaid/self promotion
    sponsorblock_music_offtopic_color = "#FF9900", -- color for unpaid/self promotion
    sponsorblock_filler_color = "#7300FF",         -- color for filler content/tangents

    -- Experimental
    show_youtube_comments = false,             -- EXPERIMENTAL - show youtube comments
    comments_path = "~/Pictures/mpv/comments", -- EXPERIMENTAL - the download path for the comment JSON file
    FORCE_fix_not_ontop = true,                -- EXPERIMENTAL - try and mitigate https://github.com/zydezu/ModernX/issues/30, https://github.com/akiirui/mpv-handler/issues/48
}
```

### Border differences

This is what disabling and enabling the border looks like:

| Border Enabled | Border Disabled |
| -------------- | --------------- |
| ![mpv_tkhXHUKNNt](https://github.com/zydezu/ModernX/assets/50119098/d2c3eb4e-5c7d-45df-ab35-6a0903c9c075) | ![mpv_rrIXTdX0Sx](https://github.com/zydezu/ModernX/assets/50119098/5573c30b-d57e-434a-b189-71dfb94b70bb) |

> [!NOTE]
> This option may vary depending on your system.

### Compact Mode

Compact mode is a setting you can enable in the configuration, it removes the skip buttons, and places that functionality within the chapter buttons, allowing for more space in the interface. Clicking the buttons will act as jumping, and shift clicking will act as skipping a chapter

| Compact Mode Enabled | Compact Mode Disabled |
| -------------- | --------------- |
| ![mpv_EIgoJwS7WX](https://user-images.githubusercontent.com/50119098/236636371-99c17ce7-443c-466e-a442-47bc3a6db573.png) | ![mpv_au7Au4oZso](https://user-images.githubusercontent.com/50119098/236636421-c247d9af-d982-4aba-9171-a4f8103eec16.png) |

> [!IMPORTANT]
> This changes the actions of the chapter back/forward buttons in the following way:
>
> - `Left mouse button` jumps forwards/backwards by 5 seconds, or by the amount set in `jump_amount`, instead of skipping to the previous/next chapter
> Please note that this option will override the `showjump` option.

### Thumbnails

To enable thumbnails on the seekbar, install [thumbfast](https://github.com/po5/thumbfast). No other step necessary.

![mpv_UzSC2z3vIt](https://user-images.githubusercontent.com/50119098/236636833-8bd0a665-7230-496f-89e8-0209de59c530.png)

## Buttons

Like the built-in script, some buttons may accept multiple mouse actions, here is a list:

> [!NOTE]
> Middle clicking performs the same function as `Shift+left mouse button`, allowing for one handed use

### Title

- `Left mouse button` show the full media title
- `Right mouse button` show the full filename

### Description (only on certain videos)

- `Left mouse button` show the full description, use `up arrow`, `down arrow` or `scroll wheel` to scroll through it
- `Tab`/`Shift+Tab` cycle through links found in the description
- `Enter` open the selected link, or close the description if no link is selected

### Seekbar

- `Left mouse button` seek to chosen position (using keyframes)
- `Shift+left mouse button` seek to the exact position
- `Right mouse button` seek to the head of chosen chapter

### Playback time

- `Left mouse button` display time in milliseconds

### Duration

- `Left mouse button` display total time instead of remaining time

### Playlist back/forward buttons

- `Left mouse button` play previous/next file
- `Right mouse button` shuffle the playlist
- `Shift+left mouse button` open the interactive playlist selector
- `Shift+right mouse button` jump to the start/end of the playlist

### Skip back/forward buttons

- `Left mouse button` go to previous/next chapter (or jump by `jump_amount` seconds in compact mode)
- `Right mouse button` jump forwards/backwards by the amount set in `jump_more_amount`
- `Shift+left mouse button` open the interactive chapter selector
- `Shift+right mouse button` go to the next chapter

### Jump back/forward buttons

- `Left mouse button` jumps forwards/backwards by 5 seconds, or by the amount set in `user_opts`
- `Right mouse button` jumps forwards/backwards by 1 minute
- `Shift+left mouse button` skips to the previous/next frame

### Audio/subtitle track buttons

- `Left mouse button/right mouse button` cycle to next/previous track
- `Shift+left mouse button` cycle to next/previous track and show track list
- `Shift+right mouse button` show track list

### Pin button

- `Left mouse button` toggle pinning (sets window title to include "(Picture-in-Picture)" and removes the border)
- `Right mouse button` toggle pinning without changing the border

### Volume

- `Left mouse button` mute/unmute video
- `Scroll wheel` change volume

### Other

- `x` cycle through audio tracks
- `c` cycle through subtitle tracks
- `C` open subtitle track selector
- `p` pin or unpin the window
- `Tab` open interactive chapter selector
- `Shift+left` go to the previous chapter
- `Shift+right` go to the next chapter
- `Ctrl+left` go to the previous file (in playlist)
- `Ctrl+right` go to the next file (in playlist)
- `b` toggle the persistent progress bar if `persistentprogresstoggle` is enabled
