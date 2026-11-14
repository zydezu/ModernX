# ModernX User Options Guide

ModernX options live in `modernx.conf` under mpv `script-opts/`. Defaults follow the ModernX core unless noted below (layouts, description, `key_bindings`, etc.).

Older `modernx.conf` files keep the same script id (`modernx`). Renames: `layout_option` → `layout` (`default`, `compact`, `mini`, `seekbar`, `original`, `reduced`); `chapter_marker_style` → `nibbles_style`; `scale_windowed` → `scalewindowed`; `vid_scale` → `vidscale`. A leftover `layout_option` is applied when `layout` is still the default (`original`).

### Configuration File Location

Create `modernx.conf` in your mpv script-opts directory:

- Linux: `~/.config/mpv/script-opts/`
- Windows: `%APPDATA%/mpv/script-opts/`
- macOS: `~/Library/Application Support/mpv/script-opts/`

## Available Options

### Language and display

| Option                    | Value           | Description                                                                                                                    |
| ------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| language                  | default         | set language (for available options, see: [Translations](https://github.com/zydezu/ModernX/blob/main/docs/TRANSLATIONS.md)) |
| layout                    | original        | set layout: `default`, `compact`, `mini`, `seekbar`, `original`, `reduced`. Images still use the image viewer layout. `original` / `reduced` are the ModernX arrangements (combined time codes, transport row). Unknown values warn and fall back to `default`. |
| icon_theme                | fluent          | set icon theme. accepts `fluent` or `material`                                                                                 |
| icon_style                | mixed           | "mixed", "filled", "outline"                                                                                                   |
| font                      | mpv-osd-symbols | font for the OSC (default: mpv-osd-symbols or the one set in mpv.conf)                                                         |
| idlescreen                | yes             | show mpv logo when idle                                                                                                        |
| window_top_bar            | auto            | show OSC window top bar: `"auto"`, `"yes"`, or `"no"` (borderless/fullscreen)                                                  |
| showwindowed              | yes             | show OSC when windowed                                                                                                         |
| showfullscreen            | yes             | show OSC when fullscreen                                                                                                       |
| showonselect              | no              | show OSC when a select menu is open                                                                                            |
| showonpause               | no              | show OSC when paused                                                                                                           |
| keeponpause               | no              | keep OSC visible while paused: `"no"`, `"bottombar"`, `"both"`                                                                 |
| greenandgrumpy            | no              | disable Santa hat in December                                                                                                  |

### OSC behaviour and scaling

| Option               | Value   | Description                                                                                                                                        |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| hidetimeout          | 2000    | time (in ms) before OSC hides if no mouse movement                                                                                                 |
| keep_with_cursor     | yes     | keep OSC visible while cursor hovers over bottom or top bar                                                                                        |
| fadeduration         | 150     | fade-out duration (in ms), set to `"0"` for no fade                                                                                                |
| fadein               | yes     | whether to enable fade-in effect                                                                                                                   |
| minmousemove         | 0       | minimum mouse movement (in pixels) required to show OSC                                                                                            |
| deadzonesize         | 0.75    | controls how much of the window ignores mouse movement for showing the osc; `0.0` always shows on movement, `1.0` only shows when directly hovered |
| deadzone_hide        | instant | hide behavior when cursor enters deadzone or leaves window: `"instant"` or `"timeout"`                                                             |
| osc_on_seek                | no      | show OSC when seeking                                                                                                                              |
| seek_resets_hide_timeout   | yes     | seeking resets the OSC hide timeout (independent of `osc_on_seek`)                                                                                 |
| osc_on_start               | both    | show OSC/window controls on start of every file (`no`, `bottom`, `top`, `both`)                                                                    |
| mouse_seek_pause           | yes     | pause video while seeking with mouse move (on button hold)                                                                                         |
| force_seek_tooltip         | no      | force show seekbar tooltip on mouse drag, even if not hovering seekbar                                                                             |
| vidscale                   | auto    | scale osc with the video. (set to `"no"` to disable)                                                                                               |
| scalewindowed              | 1.0     | osc scale factor when windowed                                                                                                                     |
| scalefullscreen            | 1.0     | osc scale factor when fullscreen                                                                                                                   |
| scale_forced_window        | 1.0     | osc scale factor when forced (no video, e.g. music files)                                                                                          |

### Elements display

| Option                  | Value            | Description                                                                      |
| ----------------------- | ---------------- | -------------------------------------------------------------------------------- |
| show_title              | yes              | show title in the OSC                                                            |
| title                   | `${media-title}` | title: `"${media-title}"` or `"${filename}"`                                     |
| dynamic_title           | yes              | use `${media-title}` when it differs from filename (URLs/audio)                  |
| title_font_size         | 24               | font size of the title text                                                      |
| truncate_title          | no               | truncate title with ellipsis if it overflows                                     |
| chapter_title_font_size | 16               | chapter title font size                                                          |
| show_chapter_title      | yes              | show chapter title                                                               |
| chapter_hover_title     | no               | while scrubbing (no thumbfast): show hovered chapter in main title               |
| chapter_hover_subtitle  | yes              | while scrubbing (no thumbfast): show hovered chapter in chapter title row        |
| chapter_above_title     | no               | show chapter above title                                                         |
| chapter_fmt             | %s               | format for chapter display on seekbar hover (set to `"no"` to disable)           |
| timecurrent             | yes              | show current time instead of remaining time                                      |
| timems                  | no               | show timecodes with milliseconds                                                 |
| unicodeminus            | no               | use the Unicode minus sign in remaining time                                     |
| time_format             | dynamic          | `"dynamic"` or `"fixed"`. shows MM:SS when possible, fixed always shows HH:MM:SS |
| time_font_size          | 16               | font size of the time display                                                    |
| cache_info              | no               | show cached time information                                                     |
| cache_info_speed        | no               | show current cache speed per second                                              |
| cache_info_font_size    | 12               | font size of the cache information                                               |
| tooltip_font_size       | 14               | tooltips font size                                                               |
| speed_font_size         | 16               | speed button font size                                                           |

### Optional keyboard pack

| Option        | Value | Description                                                                 |
| ------------- | ----- | --------------------------------------------------------------------------- |
| key_bindings  | yes   | when `yes`, register the ModernX key pack (see [CONTROLS.md](CONTROLS.md)); includes `DEL` theatre toggle |


### Description and web stats

The description line is drawn in the `original` layout. Other layouts keep their geometry; with `key_bindings=yes`, `d` still opens the scrolling view. YouTube view and like counts are fetched with yt-dlp when the file is a YouTube URL. Comments are on by default (`show_youtube_comments`); set `no` to disable.

| Option                  | Value                     | Description                                                                 |
| ----------------------- | ------------------------- | --------------------------------------------------------------------------- |
| show_description        | yes                       | metadata/stats line on local files, description on web videos               |
| show_file_size          | yes                       | include the file size in the description                                    |
| description_font_size   | 19                        | font size of the description line                                           |
| description_alpha       | 100                       | alpha of the scrolling description background                               |
| scrolling_speed         | 40                        | scroll step for the description overlay                                     |
| date_format             | %Y-%m-%d                  | metadata date format (`os.date`)                                            |
| title_youtube_stats     | yes                       | append YouTube view/like counts to the window title                         |
| show_youtube_comments   | yes                       | experimental YouTube comments                                               |
| comments_path           | ~/Pictures/mpv/comments   | download path for the comment JSON file                                     |

### Title bar settings

| Option                     | Value            | Description                                                               |
| -------------------------- | ---------------- | ------------------------------------------------------------------------- |
| show_window_title          | yes              | show window title in borderless/fullscreen mode                           |
| window_controls_title      | `${filename}`    | title bar format (`expand-text`); used when `show_window_title` is on     |
| window_title_font_size     | 26               | window title font size                                                    |
| window_controls            | yes              | show window controls (close, minimize, maximize) in borderless/fullscreen |
| window_close_button         | yes              | show close window control                                                 |
| window_min_button           | yes              | show minimize window control                                              |
| window_max_button           | yes              | show maximize window control                                              |
| windowcontrols_independent | yes              | show window controls (top bar) and bottom bar independently on hover      |

### Subtitle and OSD display settings

**IMPORTANT**: It is recommended to add the following in your `mpv.conf`, to circumvent subtitle or OSD bad positioning when watch later options are used.

```EditorConfig
watch-later-options-remove=sub-pos
watch-later-options-remove=osd-margin-y
```

| Option          | Value | Description                                    |
| --------------- | ----- | ---------------------------------------------- |
| sub_margins     | yes   | raise subtitles above the OSC when shown       |
| osd_margins     | no    | adjust OSD to not overlap with OSC             |
| dynamic_margins | yes   | update margins dynamically with OSC visibility |

### Buttons display and functionality

| Option                     | Value         | Description                                                                                                        |
| -------------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------ |
| subtitles_button           | yes           | show the subtitles menu button                                                                                     |
| secondary_subtitles_button | yes           | show the secondary subtitles menu button                                                                           |
| audio_tracks_button        | yes           | show the audio tracks menu button                                                                                  |
| compact_mode               | yes           | merge jump into `chapter_prev`/`chapter_next` (same seek bindings). Default/original/reduced use the center row; compact/mini use the jump slots. `compact_mode=no` keeps the jump buttons |
| jump_buttons               | yes           | show "jump forward/backward 10 seconds" buttons                                                                    |
| jump_amount                | 10            | change the jump amount in seconds                                                                                  |
| jump_more_amount           | 60            | change the jump amount in seconds on right click                                                                   |
| jump_icon_number           | yes           | show different icon for `5`, `10`, or `30` second jumps                                                            |
| jump_mode                  | relative      | seek mode for jump buttons: `"relative"` or `"exact"`                                                              |
| jump_softrepeat            | yes           | enable continuous jumping when holding down seek buttons                                                           |
| chapter_skip_buttons       | yes           | show the skip back and forward (chapter) buttons                                                                   |
| chapter_softrepeat         | no            | continuous chapter skip while holding chapter buttons (non-compact layouts)                                        |
| track_nextprev_buttons     | yes           | show next/previous playlist track buttons                                                                          |
| volume_control             | yes           | show mute button and volume slider                                                                                 |
| volume_control_type        | linear        | volume scale type: `"linear"` or `"logarithmic"`                                                                   |
| volumebar_unmute_on_click  | no            | unmute audio when adjusting volume slider with left click                                                          |
| playlist_button            | yes           | show playlist button: Left-click for simple playlist, Right-click for interactive playlist                         |
| hide_empty_playlist_button | no            | hide playlist button when no playlist exists                                                                       |
| gray_empty_playlist_button | no            | gray out the playlist button when no playlist exists                                                               |
| fullscreen_button          | yes           | show `fullscreen toggle` button                                                                                    |
| info_button                | yes           | show `info (stats)` button                                                                                         |
| ontop_button               | no            | show `window on top (pin)` button                                                                                  |
| ontop_in_topbar            | no            | move ontop button to top bar when ontop is active                                                                  |
| screenshot_button          | no            | show screenshot button                                                                                             |
| screenshot_flag            | subtitles     | screenshot mode: `subtitles`, `video`, `window`, `each-frame` (overrides left-click command)                       |
| save_button                | no            | show save-position-on-quit toggle (cycles the mpv property only; does **not** rewrite `mpv.conf`)                  |
| download_button            | yes           | show download button on web videos (requires yt-dlp and ffmpeg)                                                    |
| download_path              | ~/Pictures/mpv/ | default download directory for videos. [Learn more about setting paths here](https://mpv.io/manual/master/#paths). |
| ytdl_format                | *(empty)*     | optional yt-dlp args for download button; empty uses mpv `ytdl-format`                                             |
| loop_button                | no            | show `file loop` button                                                                                            |
| shuffle_button             | no            | show `shuffle` button                                                                                              |
| speed_button               | yes           | show speed control button                                                                                          |
| buttons_always_active      | none          | force buttons to always be active. can add: `playlist_prev`, `playlist_next`                                       |
| playpause_size             | 30            | icon size for the play/pause button                                                                                |
| midbuttons_size            | 24            | icon size for the middle buttons                                                                                   |
| sidebuttons_size           | 24            | icon size for the side buttons                                                                                     |
| windowcontrols_size        | 25            | icon size for the window control buttons (minimize, maximize, close)                                               |
| zoom_control               | yes           | show zoom controls in image viewer mode                                                                            |
| zoom_in_max                | 4             | maximum zoom in value                                                                                              |
| zoom_out_min               | -1            | minimum zoom out value                                                                                             |

### Colors and style

| Option                            | Value     | Description                                                                                       |
| --------------------------------- | --------- | ------------------------------------------------------------------------------------------------- |
| osc_color                         | `#000000` | accent color of the OSC and title bar                                                             |
| window_title_color                | `#FFFFFF` | color of the title in borderless/fullscreen mode                                                  |
| window_controls_color             | `#FFFFFF` | color of the window controls (close, minimize, maximize) in borderless/fullscreen mode            |
| windowcontrols_close_hover        | `#E81123` | color of close window control on hover                                                            |
| windowcontrols_max_hover          | `#53A4FC` | color of maximize window controls on hover                                                        |
| windowcontrols_min_hover          | `#43CB44` | color of minimize window controls on hover                                                        |
| title_color                       | `#FFFFFF` | color of the title                                                                                |
| seekbar_cache_color               | `#1D96F5` | color of the cache ranges on the seekbar                                                          |
| seekbarfg_color                   | `#1D96F5` | color of the seekbar progress                                                                     |
| seekbarbg_color                   | `#FFFFFF` | color of the remaining seekbar                                                                    |
| seek_handle_color                 | `#088CC9` | color of the seekbar handle                                                                       |
| seek_handle_border_color          | `#328BFF` | inner border color drawn inside the seekbar handle (set to `disable` to disable)                  |
| volumebar_match_seek_color        | no        | match volume bar color with seekbar color (ignores `side_buttons_color`)                          |
| time_color                        | `#FFFFFF` | color of the timestamps                                                                           |
| chapter_title_color               | `#FFFFFF` | color of the chapter title                                                                        |
| cache_info_color                  | `#FFFFFF` | color of the cache information                                                                    |
| side_buttons_color                | `#FFFFFF` | color of the side buttons (audio, subtitles, playlist, etc.)                                      |
| middle_buttons_color              | `#FFFFFF` | color of the middle buttons (skip, jump, chapter, etc.)                                           |
| playpause_color                   | `#FFFFFF` | color of the play/pause button                                                                    |
| held_element_color                | `#999999` | color of the element when held down (pressed)                                                     |
| hover_effect_color                | `#FFFFFF` | color of a hovered button when `hover_effect` includes `"color"`                                  |
| thumbnail_box_color               | `#FFFFFF` | color of the background for thumbnail box                                                         |
| thumbnail_box_outline             | `#000000` | color of the border outline for thumbnail box                                                     |
| nibble_color                      | `#1D96F5` | color of chapter nibbles on the seekbar                                                           |
| nibble_current_color              | `#9D96f5` | color of the current chapter nibble on the seekbar                                                |
| ab_loop_color                     | `#2596be` | color of the A/B loop range on the seekbar                                                        |
| osc_fade_strength                 | 100       | strength of the OSC background fade (0 to disable)                                                |
| fade_blur_strength                | 75        | blur strength for the OSC alpha fade. caution: high values can take a lot of CPU time to render   |
| fade_transparency_strength        | 0         | use with "fade_blur_strength=0" to create a transparency box                                      |
| window_fade_strength              | 100       | strength of the window title bar fade (0 to disable)                                              |
| window_fade_blur_strength         | 100       | blur strength for the window title bar. caution: high values can take a lot of CPU time to render |
| window_fade_transparency_strength | 0         | use with "window_fade_blur_strength=0" to create a transparency box                               |
| thumbnail_box_padding             | 4.5       | thumbnail box padding around the image                                                            |
| thumbnail_box_radius              | 5         | round corner radius for thumbnail box border (0 to disable)                                       |
| thumbnail_box_outline_size        | 1         | thumbnail box border outline size (thickness)                                                     |

### Button interaction settings

| Option                | Value               | Description                                                                                       |
| -------------------   | ------------------- | ------------------------------------------------------------------------------------------------- |
| hover_effect          | size,glow,color     | active button hover effects: `glow`, `size`, `color`, `box`; can use multiple separated by commas |
| button_hover_size     | 115                 | relative size of a hovered button if "size" effect is active                                      |
| button_held_size      | 100                 | relative size of a button when held/pressed. below 100 shrinks button when held down              |
| button_held_box_alpha | 18                  | alpha of the hover background box when a button is held down                                      |
| button_glow_amount    | 5                   | glow intensity when `"glow"` hover effect is active                                               |
| slider_hover_size         | 100                 | relative size of a hovered slider handle (100 = no size change)                                   |
| hover_effect_for_sliders  | yes                 | apply `slider_hover_size` to slider handles on hover                                              |
| tooltip_hints             | yes                 | enable tooltips for most buttons. seek and volume tooltips are always enabled                     |

### Progress bar settings

| Option                        | Value    | Description                                                                                 |
| --------------------------    | -------- | ------------------------------------------------------------------------------------------- |
| seek_handle_size              | 0        | size ratio of the seekbar handle (range: 0 ~ 1)                                             |
| seek_handle_border_size       | 0.42     | border thickness as a fraction of the handle radius                                         |
| seek_handle_border_hover_size | 0.31     | border thickness when handle is hovered (set equal to `seek_handle_border_size` to disable) |
| seekbar_height                | medium   | seekbar height preset: `small`, `medium`, `large`, `xlarge`                                 |
| seekbar_between_timers        | no       | `original` layout only: inset the seekbar beside the combined time codes                    |
| seekrange                     | yes      | show seek range overlay                                                                     |
| seekrangealpha                | 175      | transparency of the seek range                                                              |
| livemarkers                   | yes      | update chapter markers on the seekbar when duration changes                                 |
| seekbarkeyframes              | yes      | use keyframes when dragging the seekbar                                                     |
| slider_rounded_corners        | yes      | rounded corners seekbar slider                                                              |
| show_chapter_markers          | yes      | master switch for chapter nibbles/gaps on the seekbar                                       |
| nibbles_style                 | gap      | chapter nibble style: `gap`, `triangle`, `bar` or `single-bar`                              |
| nibbles_top                   | yes      | top chapter nibbles above seekbar                                                           |
| nibbles_bottom                | yes      | bottom chapter nibbles below seekbar                                                        |
| automatickeyframemode         | yes      | automatically set keyframes for the seekbar based on video length                           |
| automatickeyframelimit        | 600      | videos longer than this (in seconds) will have keyframes on the seekbar                     |
| persistent_progress           | no       | always show a small progress line at the bottom of the screen                               |
| persistent_progress_height    | 17       | height of the persistent progress bar                                                       |
| persistent_progress_toggle    | yes      | allow toggling persistent progress (key pack: `b`) even if default is off                   |
| persistent_buffer             | no       | show cached buffer status in the persistent progress line                                   |

### SponsorBlock

Requires an external script that publishes `user-data/sponsorblock/segments`.

| Option                    | Value | Description                                                                 |
| ------------------------- | ----- | --------------------------------------------------------------------------- |
| show_sponsorblock_segments | yes  | draw SponsorBlock ranges on the seekbar                                     |
| add_sponsorblock_chapters | yes   | keep `[SponsorBlock]` chapters; `no` strips them from `chapter-list`        |
| sponsor_types             | *(all)* | comma-separated categories to draw; empty = all known colors              |

### Miscellaneous settings

| Option                        | Value             | Description                                                   |
| ----------------------------- | ----------------- | ------------------------------------------------------------- |
| visibility                    | auto              | only used at init to set visibility_mode(...)                 |
| visibility_modes              | never_auto_always | visibility modes to cycle through, modes are separated by `_` |
| tick_delay                    | 0.0167            | minimum interval between OSC redraws (in seconds)             |
| tick_delay_follow_display_fps | no                | use display FPS as the minimum redraw interval                |
| FORCE_fix_not_ontop         | no                | experimental: cycle ontop twice on URL load (handler workaround) |

### Elements Position

Useful when adjusting font size or type, this will help you change the affected elements position

| Option                      | Value | Description                                                            |
| --------------------------- | ----- | ---------------------------------------------------------------------- |
| title_offset                | 20    | title vertical offset relative to seekbar                              |
| title_with_chapter_offset   | 5     | title vertical offset if a chapter title is below it                   |
| chapter_title_offset        | 18    | chapter title vertical offset relative to seekbar                      |
| chapter_above_title_offset  | 3     | chapter offset when shown above title                                  |
| time_codes_offset           | 0     | time codes vertical offset relative to seekbar                         |
| tooltip_height_offset       | 5     | tooltip height position offset                                         |
| portrait_window_trigger     | 950   | portrait window width trigger to move some elements                    |
| hide_volume_bar_trigger     | 1150  | hide volume bar trigger window width                                   |
| osc_height                  | 60    | osc height                                                             |

### Mouse Commands (User Options)

Customize the button function based on mouse actions.

| Type                          | Option                           | Function                                     |
| ----------------------------- | -------------------------------- | -------------------------------------------- |
| Title                         | title_mbtn_left_command          | `script-binding stats/display-page-5`        |
|                               | title_mbtn_mid_command           | `show-text ${path}`                          |
|                               | title_mbtn_right_command         | `script-binding select/select-watch-history` |
| Chapter title                 | chapter_title_mbtn_left_command  | `script-binding select/select-chapter`       |
|                               | chapter_title_mbtn_right_command | `show-text ${chapter-list} 3000`             |
| Seekbar                       | seekbar_wheel_up_command         | `seek 10`                                    |
|                               | seekbar_wheel_down_command       | `seek -10`                                   |
| Playlist button               | playlist_mbtn_left_command       | `script-binding select/select-playlist`      |
|                               | playlist_mbtn_right_command      | `script-binding select/menu`                 |
| Volume button                 | vol_ctrl_mbtn_left_command       | `no-osd cycle mute`                          |
|                               | vol_ctrl_mbtn_right_command      | `script-binding select/select-audio-device`  |
|                               | vol_ctrl_wheel_down_command      | `osd-msg add volume -5`                      |
|                               | vol_ctrl_wheel_up_command        | `osd-msg add volume 5`                       |
| Volume bar                    | volumebar_wheel_down_command     | `osd-msg add volume -5`                      |
|                               | volumebar_wheel_up_command       | `osd-msg add volume 5`                       |
| Audio button                  | audio_track_mbtn_left_command    | `script-binding select/select-aid`           |
|                               | audio_track_mbtn_mid_command     | `cycle audio down`                           |
|                               | audio_track_mbtn_right_command   | `cycle audio`                                |
|                               | audio_track_wheel_down_command   | `cycle audio`                                |
|                               | audio_track_wheel_up_command     | `cycle audio down`                           |
| Subtitle button               | sub_track_mbtn_left_command      | `script-binding select/select-sid`           |
|                               | sub_track_mbtn_mid_command       | `cycle sub down`                             |
|                               | sub_track_mbtn_right_command     | `cycle sub`                                  |
|                               | sub_track_wheel_down_command     | `cycle sub`                                  |
|                               | sub_track_wheel_up_command       | `cycle sub down`                             |
| Secondary subtitle button     | secondary_sub_track_mbtn_left_command | `script-binding select/select-secondary-sid` |
|                               | secondary_sub_track_mbtn_mid_command  | `cycle secondary-sid down`                   |
|                               | secondary_sub_track_mbtn_right_command | `cycle secondary-sid`                       |
|                               | secondary_sub_track_wheel_down_command | `cycle secondary-sid`                       |
|                               | secondary_sub_track_wheel_up_command   | `cycle secondary-sid down`                  |
| Play/Pause button             | play_pause_mbtn_left_command     | `cycle pause`                                |
|                               | play_pause_mbtn_mid_command      | `cycle-values loop-playlist inf no`          |
|                               | play_pause_mbtn_right_command    | `cycle-values loop-file inf no`              |
| Chapter skip buttons          | chapter_prev_mbtn_left_command   | `add chapter -1`                             |
|                               | chapter_prev_mbtn_mid_command    | `show-text ${chapter-list} 3000`             |
|                               | chapter_prev_mbtn_right_command  | `script-binding select/select-chapter`       |
|                               | chapter_next_mbtn_left_command   | `add chapter 1`                              |
|                               | chapter_next_mbtn_mid_command    | `show-text ${chapter-list} 3000`             |
|                               | chapter_next_mbtn_right_command  | `script-binding select/select-chapter`       |
| Playlist skip Buttons         | playlist_prev_mbtn_left_command  | `playlist-prev`                              |
|                               | playlist_prev_mbtn_mid_command   | `show-text ${playlist} 3000`                 |
|                               | playlist_prev_mbtn_right_command | `script-binding select/select-playlist`      |
|                               | playlist_next_mbtn_left_command  | `playlist-next`                              |
|                               | playlist_next_mbtn_mid_command   | `show-text ${playlist} 3000`                 |
|                               | playlist_next_mbtn_right_command | `script-binding select/select-playlist`      |
| Fullscreen button             | fullscreen_mbtn_left_command     | `cycle fullscreen`                           |
|                               | fullscreen_mbtn_right_command    | `cycle window-maximized`                     |
| Info button                   | info_mbtn_left_command           | `script-binding stats/display-page-1-toggle` |
| Pin (ontop) button            | ontop_mbtn_left_command          | `osd-msg cycle ontop`                        |
| Screenshot button             | screenshot_mbtn_left_command     | `osd-msg screenshot video`                   |
| Loop button                   | file_loop_mbtn_left_command      | `osd-msg cycle-values loop-file inf no`      |
|                               | file_loop_mbtn_right_command     | `osd-msg cycle-values loop-playlist inf no`  |
| Speed button                  | speed_mbtn_left_command          | `osd-msg add speed 1`                        |
|                               | speed_mbtn_right_command         | `osd-msg set speed 1`                        |
|                               | speed_wheel_down_command         | `osd-msg add speed -0.25`                    |
|                               | speed_wheel_up_command           | `osd-msg add speed 0.25`                     |

### Auto Profile

Below is an example of an auto-profile in `mpv.conf` you can use to set any of ModernX options based on certain conditions, in this case `when window is pinned or fullscreen`.

```EditorConfig
[ModernX-Custom]
    profile-desc=Apply ModernX options on pin or fullscreen
    profile-cond=ontop == true or fullscreen
    profile-restore=copy-equal
    script-opts-append=modernx-persistent_progress=yes
    script-opts-append=modernx-seekbarfg_color=#FF0000
    script-opts-append=modernx-info_button=no
    #...etc
```

More information about auto profiles available on [mpv's manual](https://mpv.io/manual/master/#conditional-auto-profiles).
