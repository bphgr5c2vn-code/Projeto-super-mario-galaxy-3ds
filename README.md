for azahar:
Play SMG-3DS Reborn in Azahar (no 3DS console required)

This guide covers the desktop version of Azahar. You can run this homebrew port on a PC without a physical 3DS. You still need your own Super Mario Galaxy USA (RMGE01) disc image in RVZ format. Neither that image nor Nintendo game assets are included.

## 1. Download and extract

1. Download the desktop emulator from the [official Azahar website](https://azahar-emu.org/) or its [official releases](https://github.com/azahar-emu/azahar/releases).
2. Install or extract Azahar for your operating system and launch it once.
3. Download `SMG-3DS-development-2026-10-31.zip` from this project's Releases and extract it. Locate `3ds/SMG-3DS.3dsx`.

Use the standalone desktop application for these instructions. Android and RetroArch have different menus and were not validated for this build. The development build was tested with Azahar 2126.2 on Windows.

## 2. Find the emulated SD card

Use Azahar's **File** menu to open its user folder (**Open Azahar Folder**), then open the `sdmc` directory. Some versions also provide an **Open SDMC Folder** command. Menu wording may differ with language/version.

On Windows, the normal user folder is `%APPDATA%/Azahar`. A portable installation can instead use a `user` folder beside the emulator executable. Prefer the folder opened by Azahar itself so you do not copy files to an unused installation.

Create the following structure inside that `sdmc` folder:

```text
sdmc/
└── 3ds/
    ├── SMG-3DS.3dsx
    └── SMG-3DS/
        ├── game.rvz
        └── settings.ini
```

Copy `SMG-3DS.3dsx` from the extracted download. Copy your USA RVZ into `SMG-3DS` and rename it exactly `game.rvz`. Enable file extensions in your file manager to avoid names such as `game.rvz.rvz`.

`settings.ini` is optional. For a mouse-controlled touch pointer, create a plain-text file with this content (do not save it as `.ini.txt`):

```ini
pointer=stylus
```

An existing configuration can be kept; change only the pointer setting if needed. Do not add development-stage or skip-story flags for normal play.

## 3. Configure Azahar

Open the emulator's configuration window:

- Enable **New 3DS mode** in the system settings.
- Keep **CPU clock speed at 100%** and emulation speed at normal/100%.
- Start with **internal resolution 1×** in the graphics settings. Higher resolution can be tried later if your PC has headroom.
- Keep audio enabled. Leave other emulator settings at their defaults initially.
- In **Controls**, map the Circle Pad and A, B, X, Y, L, R, ZL, ZR, Start and Select to your keyboard or controller. These names refer to emulated 3DS buttons, not necessarily the same letters on your keyboard.

The port targets at most 30 rendered FPS. Its gameplay simulation and audio keep their normal timing. Do not use emulator fast-forward or CPU overclock as a way to change animation speed.

## 4. Launch the port

1. Choose **File → Load File** (or the equivalent Open command) and select `SMG-3DS.3dsx`.
2. Wait for startup; the title can take roughly a minute to appear, particularly on a first run.
3. When Galaxy asks for Wii A + B at the title, press your mapped **3DS A + R together**.
4. Select a save slot and start playing. In stylus mode, use the mouse on the lower/touch screen for the pointer.

**Open the `.3dsx` in Azahar, not the `.rvz`.** The running port reads `game.rvz` from its emulated SD card. A Wii emulator is not needed for this workflow.

| Action | Emulated 3DS input |
| --- | --- |
| Move | Circle Pad |
| Jump | A or B |
| Spin | X or Y |
| Crouch / ground pound | L |
| Shoot Star Bits | R |
| Camera behind Mario | ZL |
| Recenter pointer | ZR |
| Pause | Start |
| Wii Minus | Select |

These are the port's defaults. An existing `settings.ini` may override them. Saves are stored under `sdmc/3ds/SMG-3DS/nand/`; keep a backup before updating.

## Troubleshooting

- **Missing disc / cannot load game:** check the active `sdmc` folder, exact filename and USA RMGE01 image. Keep the complete RVZ; the port needs the actual disc data, not a shortcut or an empty file.
- **The RVZ is rejected by Azahar:** load the `.3dsx` instead; the RVZ is input data for the port.
- **Title does not react:** map both 3DS A and R, then hold them together. Keyboard letter A is not automatically the emulated A button.
- **Pointer does not react:** use `pointer=stylus`, restart the port and click/move on the lower screen. Check the file is really named `settings.ini`.
- **Slow gameplay:** confirm New 3DS mode, normal emulation speed and 1× resolution. Loading and busy scenes can dip below 30 FPS. Emulator results depend on the PC and are not measurements of console performance.
- **Silent audio:** check Azahar's volume, mute state and output device. If the port reports an NDSP/DSP initialization error, retain that message and your emulator version for a bug report; audio support can depend on the emulator setup. This package does not supply Nintendo DSP firmware.
- **Characters differ from the project's private test screenshots:** the public download does not contain extracted DS models or animation banks. Optional overrides must be generated locally from your own assets using the repository tools. Without them the original RVZ resources are used. The 75% Mario pose clock applies specifically to the optional DS Mario animation bank.
- **Freeze or graphical bug:** note the emulator version, scene, action and any on-screen error. This is a development build; full-story compatibility has not been established.

## References

- [Official Azahar website and downloads](https://azahar-emu.org/)
- [Azahar desktop menu definitions](https://github.com/azahar-emu/azahar/blob/master/src/citra_qt/main.ui)
- [Azahar user-folder handling](https://github.com/azahar-emu/azahar/blob/master/src/common/file_util.cpp)
- [Port controls and runtime setup](HANDOFF.md#running-it)

Nintendo owns the original games, characters and assets. This unofficial project is not affiliated with or endorsed by Nintendo.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

For new 3ds/2ds:

SMG-3DS Reborn — development build (2026-10-31)

Target: New Nintendo 3DS, New Nintendo 3DS XL and New Nintendo 2DS XL.
Install SMG-3DS.3dsx in /3ds/ on your SD card.
Provide your own Super Mario Galaxy USA (RMGE01) RVZ at /3ds/SMG-3DS/game.rvz.
Run the executable with the Homebrew Launcher.

This is unfinished software. The rendering target is 30 FPS; gameplay and audio retain normal timing. Emulator results do not guarantee performance or compatibility on physical hardware or throughout the full story. Back up existing saves before testing a development build.

No RVZ, DS ROM, extracted models, textures, animation banks or music is bundled. Optional DS character overrides must be generated locally from your own assets using the repository tools. Without those overrides the port reads the original resources from your RVZ; the 75% visual animation speed applies specifically to the optional DS Mario bank.

Nintendo owns the original games, characters and game assets. This unofficial fan project is not affiliated with or endorsed by Nintendo. Original SMG-3DS and Petari contributors retain their credits. Source license: GPL-3.0; see LICENSE and the repository for source and build instructions.
Source: https://github.com/bphgr5c2vn-code/smg-3ds

PC / Azahar: no physical 3DS is needed to run this homebrew in the desktop emulator. Read AZAHAR.md for the complete setup. Load SMG-3DS.3dsx in Azahar, and place your USA game.rvz under its active sdmc/3ds/SMG-3DS/ directory.
