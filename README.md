# Archived
## The [upstream base repo](https://github.com/hl2guide/better-mpv-config) has now been reworked and now uses much less performance intensive shaders (similar to the ones used here) and thus, I have no time nor motivation to maintain this fork
### Please use the base repo, thank you

<details><summary><h2>Old README</h2></summary>

# better-mpv-config (vbajs's fork)

## Intro

This is an improved MPV Media Player configuration file (and shaders folder) that:

- has useful defaults
- offers profiles
- hides the window title bar
- auto-hides the cursor after 400ms
- saves the seekbar position on exit
- uses an large RAM cache
- normalizes audio (disabled by default, revertable)
- sets Color Space, Dithering, Debanding, Subtitles
- sets Anti-Ringing and Upscaling & Processing
- now uses shaders for improved visuals
- improves profiles for https and http protocols
- adds no additional cruft...
    + vbajs's changes:
     - makes mpv remain open after playback is over
     - auto subtitle file pathing
     - acme-0.5x is used as the only shader for 4K to ease downscaling 
     - SSimSuperRes is now used instead of FSRCNNX
     - disable motion interpolation
     - disable autoplay (inherited from base repo's v3 config)
     - use max quality for HLS streams (inherited from base repo's v3 config)
     - force videos to be seekable (inherited from base repo's v3 config)
     - prefetch playlists (inherited from base repo's v3 config)
     - adds keybinds (See [Keybinds](https://github.com/vbajs/better-mpv-config#keybinds) for more info)

This fork was made to ease performace at the trade of slightly decreased visuals, it was tested on a Ryzen 5 3500U APU that uses Vega 8 graphics is outputting to a 1080p display. 

If you are not using an APU and actually have a decent CPU+GPU, please do not use this fork and use the [base repo](https://github.com/hl2guide/better-mpv-config) instead.

## Credits

Thanks to all the original creators for making awesome shaders and extra work:

* [FSRCNNX](https://github.com/xzpyth/mpv-config/blob/main/shaders/FSRCNNX_x2_8-0-4-1.glsl)
* [KrigBilateral by Shiandow](https://gist.github.com/igv/a015fc885d5c22e6891820ad89555637)
* [SSimSuperRes by Shiandow](https://gist.github.com/igv/2364ffa6e81540f29cb7ab4c9bc05b6b)
* [SSimDownscaler by Shiandow](https://gist.github.com/igv/36508af3ffc84410fe39761d6969be10)
* [acme-0.5x](https://gist.github.com/bjin/15f307e7a1bdb55842bbb663ee1950ed)

Includes selected lines from Mike Connelly's work on MPV.

* GitHub Repo: https://github.com/classicjazz/mpv-config
* Article: https://freetime.mikeconnelly.com/archives/5371

As well as selected lines from Kokomins blogs, LightArrowsEXE's mpv.conf and iamscum's guide.

* Article: https://kokomins.wordpress.com/2019/10/14/mpv-config-guide/#external-shaders

* Article: https://iamscum.wordpress.com/guides/videoplayback-guide/mpv-conf/

* Github Repo: https://github.com/LightArrowsEXE/dotfiles/blob/master/mpv/.config/mpv/mpv.conf

## Requirements

* official MPV Player: https://mpv.io/
* a PC with at least 4GB of RAM
* a PC with integrated (CPU) or discreet GPU (card)

![usage preview](https://raw.githubusercontent.com/hl2guide/better-mpv-config/master/preview%20image.png)

## Configuration

### Windows Users

Download either of the zip files from the releases section (Old releases will be marked as pre-release, latest will be marked as latest):

`mpv-config.zip` should be extracted at the location `%APPDATA%/mpv/`

`mpv-alongside-config.zip` should be extracted at the location of where _mpv.exe_ is stored, you can find out by entering the following command into cmd `where mpv` (if it can recongize `mpv` command)

You will need to take out the files from the _alongside_ folder found in the zip to outside to the root directory (In which is where your _mpv.exe_ is stored)

* Additional for better video playback:

    Go to windows settings>system>display>scroll down to graphic settings
    Then you'll need to browse to the path of where mpv.exe is stored and choose high performance
    
![graphic settings example](https://raw.githubusercontent.com/vbajs/better-mpv-config/master/graphic%20settings%20example.jpg)

### Linux Users

* You can put all of the options in configuration files which will be read every time mpv is run.
* The system-wide configuration file 'mpv.conf' is in your configuration directory (e.g. `/etc/mpv` or `/usr/local/etc/mpv`).
* The user-specific one is `~/.config/mpv/mpv.conf`.

### Mac Users

This config will need your own additional work if you happen to use a Mac PC (since Macs only support OpenGL).

I don't own any Mac PCs to test it so even if I wanted to I could not.

## Usage

* Extract to the correct location (as above) for your Operating System (pick between _mpv.conf_ and _alongside_, renaming to _mpv.conf_, same goes for _input.conf_).
* Next time MPV is launched, and thereafter the settings should load. (command line or GUI)
* An initial seek time of 1 second is normal (tested on an old PC with 4 CPU cores) due to new shaders

### Vital Notes

If you run into playback issues then comment the __uncommented 2 lines__ and save changes to the file 'mpv.conf'.

You can also read into the 'mpv.conf' file for the (revertable) options

## Custom Profiles

This config uses specific naming convensions for shorter easier typing.

By default MPV plays video streams at the highest available quality (even 4K on a 1080p display).

Using my custom profiles allows for finer grain control over quality and framerate.

### Naming Convensions

Profiles use the format: `\<letter\>\<number\>`

The _letter_ referring to the video's __quality level__ and the _number_ the __FPS (frames per second)__.

| 480p | 720p | 1080p | 1440p (2.5K) | 2160p (4K) | 4320p (8K) |
| ------ | ------ | ------ | ------ | ------ | ------ |
| Very Low  | Low | Medium | High | Ultra | Supreme |

| Very Low  | Low | Medium | High | Ultra | Supreme |
| ------ | ------ | ------ | ------ | ------ | ------ |
| V | L | M | H | U | S |

| 30 FPS | 60 FPS |
| ------ | ------ |
| 30 | 60 |

(The config file now uses meaning descriptions so MPV's OSD and console will be more informative)

## Examples

__Using the "profile" switch__

#### Windows

4K @ 60 FPS:

`mpv.exe --profile=U60`

4K @ 30 FPS:

`mpv.exe --profile=U30`

1080p @ 60 FPS:

`mpv.exe --profile=M60`

1080p @ 30 FPS:

`mpv.exe --profile=M30`

#### Linux

Same as above but remove the `.exe` in the examples.

## Keybinds

This config adds the following keybinds that do the following

| Keybind       | Action        |
| ------------- |:-------------:|
| k             | Shuffle/Unshuffle files order |
| Alt+k         | Shuffles playlist order |
| D (Shift+d) 	| Enable/Disable debanding |
| Q (Shift+q)   | Don't save/save playback position on quit |
| T (Shift+t)	| Make the mpv window stay/dont stay ontop of other windows
| Alt+a         | Enable/Disable Audio normalization |
| Alt+7         | Toggle KrigBilateral shader on command |
| Alt+8         | Toggle acme-0.5x shader on command |
| Alt+9         | Disable **all** shaders |
