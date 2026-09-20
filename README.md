A guide on how to **download** and **install mods** in [PEAK](https://store.steampowered.com/app/3527290/PEAK/) on PC.

PEAK is built in Unity, which means [BepInEx](https://github.com/BepInEx/BepInEx) does the loading and [Thunderstore](https://thunderstore.io/c/peak/) hosts basically the entire mod scene. There are well over two thousand PEAK packages on there now, and the pace has not really slowed since launch.

We install two mods in this guide rather than one, because installing a second mod is where people actually get stuck:

* [PEAK Unlimited](https://thunderstore.io/c/peak/p/glarmer/PEAK_Unlimited/) - raises the four player cap.
* [Piggyback](https://thunderstore.io/c/peak/p/Roose/Piggyback/) - lets you carry teammates who have not passed out.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-peak/)

## Table Of Contents
* [Requirements](#requirements)
* [A Note On Platforms](#a-note-on-platforms)
* [The Two Pieces](#the-two-pieces)
* [Installing With Gale](#installing-with-gale)
    * [Adding A Second Mod](#adding-a-second-mod)
* [Installing With r2modman Or Thunderstore Mod Manager](#installing-with-r2modman-or-thunderstore-mod-manager)
* [Installing Manually](#installing-manually)
    * [BepInEx First](#bepinex-first)
    * [Then The Mods](#then-the-mods)
* [Installing With The TMC App](#installing-with-the-tmc-app)
* [Lobbies And Matching Mod Lists](#lobbies-and-matching-mod-lists)
* [Configuring Mods](#configuring-mods)
* [Updating, Disabling And Uninstalling](#updating-disabling-and-uninstalling)
* [Troubleshooting](#troubleshooting)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
* A PC running **Windows 10** or later. Linux via Proton works with one extra setting, covered further down.
* **PEAK** on Steam.
* A couple of hundred MB of free space for a normal mod list.
* An archive tool such as [7-Zip](https://www.7-zip.org/) for manual installs.

PEAK has no anti-cheat and modding it carries no ban risk.

## A Note On Platforms
PEAK is a **Windows only, Steam only** release. There is no PlayStation, Xbox or Switch version, and nothing in this guide applies to anything other than the PC build.

Linux players can run PEAK through Proton and mods do work, with one extra step described in the [Troubleshooting](#troubleshooting) section.

## The Two Pieces
Every PEAK mod install is the same two pieces stacked on each other.

1. **[BepInExPack for PEAK](https://thunderstore.io/c/peak/p/BepInEx/BepInExPack_PEAK/)** goes in the game folder. It hooks the game at launch and is what actually loads mods.
2. **The mods** go into `BepInEx/plugins`, and BepInEx picks them up when the game starts.

Note that PEAK uses its own BepInEx pack, `BepInExPack_PEAK`, rather than the generic one you may have installed for some other game. Use the PEAK one.

Beyond that, some mods depend on shared libraries. [PEAKLib](https://thunderstore.io/c/peak/p/PEAKModding/PEAKLib_Core/) shows up as a dependency for a lot of the bigger content mods. Neither of our two examples needs it, but you will run into it soon enough, and it is the reason a mod manager saves you time.

## Installing With Gale
[Gale](https://thunderstore.io/c/peak/p/Kesomannen/GaleModManager/) is small, quick and does not need an Overwolf account, which makes it an easy default for PEAK.

1. Download Gale from [Thunderstore](https://thunderstore.io/c/peak/p/Kesomannen/GaleModManager/) or [GitHub](https://github.com/Kesomannen/gale/releases) and install it.
2. Open Gale and choose **PEAK**.
3. Let it detect your Steam install, or point it at the game folder yourself.
4. Open **Browse mods** and search for **PEAK Unlimited**.
5. Click **Install**. BepInExPack_PEAK is installed alongside it as a dependency.
6. Click **Launch game (modded)**.

### Adding A Second Mod
This is the bit worth showing, because it is where the mental model clicks.

1. Go back to **Browse mods**.
2. Search for **Piggyback** and click **Install**.
3. Look at **Installed mods**. You should now have three entries: BepInExPack_PEAK, PEAK Unlimited and Piggyback.
4. Launch modded again.

You do not reinstall BepInEx, you do not start a new profile, and you do not need to care about load order. BepInEx loads whatever is in `plugins` and mods sort themselves out. Adding mod number twenty works exactly the same way as adding mod number two.

**TIP** - There are several mods on Thunderstore called Piggyback. The one this guide uses is by **Roose**, which is the one with a million or so downloads.

## Installing With r2modman Or Thunderstore Mod Manager
If you would rather use [r2modman](https://thunderstore.io/c/peak/p/ebkr/r2modman/) or [Thunderstore Mod Manager](https://www.overwolf.com/app/Thunderstore-Thunderstore_Mod_Manager), the flow is the same with different labels:

1. Install the manager and select **PEAK**.
2. Create a profile, or use **Default**.
3. Open **Online** or **Get mods**, search for each mod, and use **Download with dependencies**.
4. Click **Start modded**.

r2modman is the option to reach for on Linux or macOS, though PEAK itself has no macOS build.

## Installing Manually
Find the game folder first. Right-click **PEAK** in Steam, then **Manage** and **Browse local files**:

```
C:\Program Files (x86)\Steam\steamapps\common\PEAK
```

### BepInEx First
1. Open [BepInExPack_PEAK](https://thunderstore.io/c/peak/p/BepInEx/BepInExPack_PEAK/) and click **Manual Download**.
2. Extract the zip somewhere that is not the game folder.
3. Open the extracted folder, then open `BepInExPack_PEAK` inside it.
4. Copy the **contents** of that folder into the PEAK folder. `BepInEx`, `doorstop_config.ini` and `winhttp.dll` should end up beside `PEAK.exe`.
5. Run the game once and quit, so BepInEx creates `BepInEx/plugins`.

**WARNING** - Copy the contents, not the containing folder. A path like `PEAK\BepInExPack_PEAK\BepInEx\` will not load anything.

### Then The Mods
1. Download [PEAK Unlimited](https://thunderstore.io/c/peak/p/glarmer/PEAK_Unlimited/) and [Piggyback](https://thunderstore.io/c/peak/p/Roose/Piggyback/) with **Manual Download**.
2. Extract each one.
3. Copy the `.dll` from each into `PEAK\BepInEx\plugins`.

Both can sit loose in `plugins` together. Mods that ship a folder of assets should have the whole folder copied in instead, which BepInEx handles fine.

## Installing With The TMC App
Last on the list is our own: [the TMC App](https://moddingcommunity.com/tmc-app), a mod manager and server browser we are building. Its **sandboxes** work like the profiles above, named mod lists per game with their own load order and deployment method, and swapping between them costs nothing because nothing is re-downloaded.

**PEAK is not in its supported games list yet.** Adding a game means writing four JSON files rather than any code, so it is not a large piece of work and we would like to get to it.

Fair warning before you do go looking: **the app is in very early development.** We say so in its README and we will say so here. Plenty of it is only partially tested, so use it next to Gale rather than instead of it for now. If you try it and something goes wrong, telling us is genuinely the most helpful thing you could do at this stage.

The app is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). Bugs and feature requests belong in [the issue tracker](https://github.com/modcommunity/tmc-app/issues), pull requests are welcome, and the repository documents the per-game format if you want to add PEAK support yourself.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Lobbies And Matching Mod Lists
PEAK is four player co-op, and gameplay mods normally need to be on every machine in the lobby rather than just the host's.

PEAK Unlimited is the obvious case. It raises the player cap, so a player without it will not be able to join a lobby running above four. Piggyback changes how a shared interaction behaves, so it needs to match too.

Export a profile and hand it round rather than comparing lists by hand:

* **Gale**: **Profile**, then **Export**, giving you a code or a file.
* **r2modman / Thunderstore Mod Manager**: the profile menu, then **Export as code** or **Export as file**.

The importer ends up on the same mods at the same versions, which is what actually matters.

**NOTE** - Cosmetic mods and personal quality of life tweaks are usually client-side and safe to run alone. The mod's Thunderstore page will normally say. When it does not, assume it needs to match.

## Configuring Mods
Most PEAK mods write a config file the first time they run. You will find them here:

```
PEAK\BepInEx\config
```

Each is a plain text `.cfg` you can edit in Notepad. PEAK Unlimited's config is where you set the actual player cap, so it is one you will probably want to open.

If you would rather not edit text files by hand, Gale and r2modman both have a config editor built in that reads and writes the same `.cfg` files from inside the manager.

## Updating, Disabling And Uninstalling
Managers flag outdated mods in the installed list and update them in a click. Toggling a mod off leaves its files alone so you can flip it back on; uninstalling deletes them.

By hand, remove the `.dll` from `BepInEx/plugins`. To go fully vanilla, delete `BepInEx`, `doorstop_config.ini` and `winhttp.dll` from the game folder. Verifying files in Steam does not remove them, because Steam has no record of files it did not put there.

**TIP** - PEAK gets updates fairly regularly, and a game patch will break mods until authors rebuild them. If everything stops working right after an update, that is almost certainly what happened.

## Troubleshooting
**Mods do nothing and there is no BepInEx console.** Either BepInEx is in the wrong place or you launched PEAK from Steam. Launch from your mod manager.

**One mod loads, another does not.** Read the BepInEx console. A missing dependency or a mod built for an older PEAK version are the two usual causes.

**Cannot join a friend's lobby.** Mod lists do not match. Import their exported profile.

**Crash on startup.** Pull everything out of `BepInEx/plugins`, confirm the game starts clean, then add mods back in halves until you find the culprit.

**Stuttering with more than four players.** PEAK Unlimited pushes the game past what it was tuned for. [CrossplayStutterFix](https://thunderstore.io/c/peak/p/Rombusz/CrossplayStutterFix/) is a commonly used companion mod for exactly this.

**Linux and Proton.** BepInEx needs a DLL override. Set PEAK's Steam launch options to `WINEDLLOVERRIDES="winhttp=n,b" %command%`. Gale and r2modman set this themselves when you launch through them.

## Conclusion
PEAK modding is about as painless as it gets. Install Gale, install the mods you want, and launch through Gale rather than Steam. BepInEx is handled for you and stacking more mods on top needs no extra thought.

The only real gotcha is the co-op one: everyone in the lobby needs the same gameplay mods, and exporting a profile is much faster than working that out the hard way at eleven at night.

And if you have a few minutes spare, the [TMC App](https://github.com/modcommunity/tmc-app) is open source, very early in development, and any feedback on it is appreciated.

## See Also
* [PEAK on Thunderstore](https://thunderstore.io/c/peak/)
* [PEAK Modding Wiki](https://peakmodding.github.io/) - Aimed at mod authors, and a good read if you want to make one.
* [PEAK Modding Discord](https://discord.gg/SAw86z24rB)
* [BepInEx documentation](https://docs.bepinex.dev/)
* [TMC App](https://github.com/modcommunity/tmc-app)

We keep this guide updated as much as we can, but PEAK and its mod loader both change over time. If you hit an instruction that no longer matches reality, please report it or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-peak/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or want help with anything modding related!
