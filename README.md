# l4d2-linux-patches

> [!NOTE]
> Steam Guide: https://steamcommunity.com/sharedfiles/filedetails/?id=3269932221

Various patches and instructions to fix multiple issues with the Linux native build of Left 4 Dead 2. List of patched issues includes:

 - Fire bullets crashing the game by shooting the Tank (requires launch options below to enable)
 - Missing fonts required for checkboxes, etc.
 - Broken Chromium Embedded Framework
 - Mouse not locking in the center
 - Main Menu background not changing at all
 - Enable Vulkan
 - Wayland fixes
 - Audio latency fixes
 - Nvidia crashing fix

# Install

### Requirements

- Read fully, I see a lot of people on ProtonDB miss the launch options for the fire bullet fix.

### Optional Requirements

The lib32-harfbuzz package on your distro, see the following common packages:

- Arch-based:

`sudo pacman -S lib32-harfbuzz harfbuzz`

- Debian/Ubuntu-based (Untested)

`sudo apt install harfbuzz:i386`

- Fedora-based

`sudo dnf install harfbuzz`

If you have a different package manager (eg. Nix), just look it up or build harfbuzz with 32-bit support.

### Installation

> [!NOTE]
> You should be using the native build, not Proton.

1. Click the code button, then click download ZIP.
2. Extract the zip with any program.
3. Go to steam, right click Left 4 Dead 2 in the game list: Manage > Browse Local Files.
4. Copy the contents within the `l4d2-linux-patches-main` folder (excluding the README.md and LICENSE) to the main `Left 4 Dead 2` folder.
5. [*Optional*] Navigate to `Left 4 Dead 2/bin` and delete `libharfbuzz.so.0`. If you do this, you should have harfbuzz installed on your system for the CEF to be functional.
6. Go back to steam, right click Left 4 Dead 2 in the game list: Properties > Launch Options. Add the following: `PULSE_LATENCY_MSEC=60 %command% +map credits +mp_gamemode gunbrain +snd_mixahead 0.056 -vulkan -novid -background $(shuf -i 1-5 -n 1)`
7. Launch the game and confirm you get a loading screen with `Joining a Disabling Tracers... game.`
8. Navigate to Options > Keyboard/Mouse > Raw Mouse Input > Disabled. Also turn off subtitles as it can rarely crash on certain custom campaigns.
9. If so, success! Make sure to set `Options > Audio > Speaker Configuration > Headphones` each time you launch the game.

# Q&A

### I have a Nvidia Graphics Card and I'm crashing when I launch the game!

1. Open steam, right click Left 4 Dead 2 > Manage > Browser Local Files
2. Open hl2.sh with a text editor and find the line: `export __GL_THREADED_OPTIMIZATIONS=1`
3. Change 1 to 0 and save the file

### I'm on Wayland and the game doesn't launch/My mouse still refuses to lock into the center/Clicking with the mouse lags the game

Try adding the following to your launch options: `SDL_VIDEODRIVER=wayland STEAM_COMPAT_RUNTIME_SDL2=1`

If you're mouse still refuses to lock in the center or stop lagging the game, try using gamescope: `gamescope -f -W 1920 -H 1080 --force-grab-cursor -- [Rest of the launch options]`

### I can't import my spray, it gives me a error!

> [!NOTE]
> You can use [VTF Spray Converter](https://rafradek.github.io/Mishcatt/) to make a spray to use in-game.

1. Create a VTF file to use as your spray (use the tool above)
2. Copy the .vtf file to `Left 4 Dead 2/left4dead2/`
3. Open L4D2, Navigate to Options > Multiplayer
4. Click Import Spray, then type the exact name of your file (with the file extension) into the file name box and press enter. Example: `cat.vtf` > Enter
5. You should get an error, "Unable to write output spray file. It's possible the current user doesn't have permission."
6. Close L4D2 and navigate to `Left 4 Dead 2/left4dead2/materials/vgui/logos/custom`, create the folders if they don't exist.
7. Copy your .vtf file into the folder, where a .vmt of the same name exists. Leave the vtf in your main `left4dead2` there.
8. Re-open L4D2 and instead of importing the spray, click the dropdown and select custom logo. Type the exact name of the vtf file (e.g. `dog.vtf`) into the text box and press enter.

# Credits
- [RF (Recycle_Bin)](https://steamcommunity.com/profiles/76561198039186809) - [Fire Bullet Fix](https://www.gamemaps.com/details/30880) on GameMaps
- [gabusan](https://steamcommunity.com/id/proprocrastinator) - Background shuffle command
- [Rusty Pancakes](https://steamcommunity.com/id/RustyPancakes) - Spray import fix
- [Mono](https://steamcommunity.com/id/mono2718) - Depot Method for libmiles.so (it was in this guide once, but this bug was patched long ago)
- [Adrian Tepez](https://steamcommunity.com/id/adriantepez) - Wayland fixes, Nvidia fixes
- [SiberianLeon](https://steamcommunity.com/id/CallMeLeonidas) - Audio latency fixes, Wayland fixes
