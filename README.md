# better-mpv-config (vbajs's fork)

## Intro

This is an improved MPV Media Player configuration file (and shaders folder) that:

- has useful defaults
- offers profiles
- hides the window title bar
- auto-hides the cursor after 1 second
- saves the seekbar position on exit
- uses an extra large RAM cache
- normalizes audio (disabled by default, revertable)
- sets Color Space, Dithering, Debanding, Subtitles
- sets Motion Interpolation, Anti-Ringing and Upscaling & Processing
- now uses shaders for improved visuals
- improves profiles for https and http protocols
- adds no additional cruft...
    + vbajs's changes:
     - makes mpv remain open after playback is over
     - nerfed shaders and scaling options (revertable)
     - auto subtitle file pathing
     - use GPU Next (will be needed to be disabled if you are not using latest mpv git verison, see Vital Notes for more info)
     - HW decoding disabled by default (revertable)

This fork was made to ease performace at the trade of slightly decreased visuals, it was tested on a Ryzen 5 3500U APU that uses Vega 8 graphics. If you are not using an APU and actually have a decent CPU+GPU, please do not use this fork and use the [base repo](https://github.com/hl2guide/better-mpv-config) instead.

## Credits

Thanks to all the original creators for making awesome shaders and extra work:

* [FSRCNNX](https://github.com/xzpyth/mpv-config/blob/main/shaders/FSRCNNX_x2_8-0-4-1.glsl)
* [KrigBilateral by Shiandow](https://gist.github.com/igv/a015fc885d5c22e6891820ad89555637)
* [SSimSuperRes by Shiandow](https://gist.github.com/igv/2364ffa6e81540f29cb7ab4c9bc05b6b)
* [SSimDownscaler by Shiandow](https://gist.github.com/igv/36508af3ffc84410fe39761d6969be10)
* [ACME-0.5x](https://gist.github.com/bjin/15f307e7a1bdb55842bbb663ee1950ed)

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

Download repo as a ZIP via the "Code" button then extract the ZIP in the releases section to the location: `%APPDATA%/mpv/`

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

* Extract to the correct location (as above) for your Operating System (pick between _mpv.conf_ and _alongside_, renaming to _mpv.conf_).
* Next time MPV is launched, and thereafter the settings should load. (command line or GUI)
* An initial seek time of 1 second is normal (tested on an old PC with 4 CPU cores) due to new shaders

### Vital Notes

If you are gettig audio playback only/no vo error then either use latest mpv git verison or change the ``vo=gpu-next`` line to ``vo=gpu``.

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
