# l4d2-linux-patches
Various patches to fix multiple issues with the Linux native build of Left 4 Dead 2. List of patched issues includes:

 - Fire bullets crashing the game by shooting the Tank
 - Missing fonts
 - Broken CEF
 - Mouse not locking in the center
 - Main Menu Background not changing at all
 - Ideal launch options (Vulkan)
 - Crashing in some campaigns
 - Some other random console error

# Install

> [!WARNING]
> Ideally you should do this on a fresh installation of Left 4 Dead 2 (to avoid potential issues), but you can do this on a modified install.

> [!NOTE]
> Skip step 6 and 7 if you don't want to fix the HTML within Left 4 Dead 2. It can be obnoxious on malicious servers (Lewd 4 Dead).

1. Click the code button, then click download ZIP.
2. Extract the zip with any program.
3. Go to steam, right click Left 4 Dead 2 in the game list: Manage > Browse Local Files.
4. Copy the contents within the `l4d2-linux-patches-main` folder (excluding the README.md and LICENSE) to the main `Left 4 Dead 2` folder.
5. Navigate to `Left 4 Dead 2/bin` and delete `libharfbuzz.so.0`.
6. Make sure `lib32-harfbuzz` is installed on your system. Look up `harfbuzz 32 bit DISTRO NAME` to find the relevant package.
7. Go back to steam, right click Left 4 Dead 2 in the game list: Properties > Launch Options. Add the following: `+map credits +mp_gamemode gunbrain -vulkan -novid -background $(shuf -i 1-5 -n 1)`
8. Launch the game and confirm you get a loading screen with `Joining a Disabling Tracers... game.`
9. Navigate to Options > Keyboard/Mouse > Raw Mouse Input > Disabled
10. If so, success! Make sure to set `Options > Audio > Speaker Configuration > Headphones` each time you launch the game.

# Additional Guides

### Importing your spray

> [!NOTE]
> You can use [VTF Spray Converter](https://rafradek.github.io/Mishcatt/) to make a spray to use in-game.

1. Create a VTF file to use as your spray (use the tool above)
2. WIP

# Credits
RF (Recycle_Bin) - [Fire Bullet Fix](https://www.gamemaps.com/details/30880) on GameMaps
[gabusan](https://steamcommunity.com/id/proprocrastinator) - Background shuffle command
[Rusty Pancakes](https://steamcommunity.com/id/RustyPancakes) - Spray import fix