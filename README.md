# Genesis-Plus-GX-Cyclone

This is a modification of Genesis Plus GX which can play enhanced Sega Genesis Flashback games. For more info, see [the dedicated page](https://karmic128.neocities.org/sgflashback/).

My own comments will be denoted in `/*** ***/` comment blocks.

## Known issues/unknowns

The following issues exist due to lack of testing:
* The Z80->VDP write handler is completely unmodified, so writes will always go to standard CRAM.
* I assume that nametable priority has no effect in bitmap mode, and that sprites always go in front of the bitmap. This may not be true.
* Not sure how bitmap mode works in 32-column mode. Currently the rightmost 8 columns are just cut off, but it may "reinterpret" the bitmap data so that each row is only 256 bytes long.
* I assume that bitmap mode requires both bits 7 and 6 in register $18 to be activated. It might just need bit 6.
* Not sure what happens when cyclone mode is turned off when a VDP address is >$10000. Currently I just AND the current address with $ffff.
* Not sure if cyclone mode requires the M5 bit to be set in register #1. Currently it does not.
  * The games try doing DMA with the cyclone bit on and M5 bit off, and they will be glitched if cyclone mode requires both bits to be set.
* Not sure how shadow/highlight works in cyclone mode. Currently it has no effect.
* Not sure what happens when cyclone mode is turned off then back on again when the background color register is >$40. Currently the value will just be masked with $3f by turning it off.

The following emulation issues exist:
* Jack's Pea has flickering scrolling. The jerkiness is in the original, though.
* After losing a game of Cross the Road, BG A (the logo and cloud surrouding "press start") is not centered.
* The sound samples which sound weird on the actual console sound OK in the emulator. Kind of seems like an anti-fix, so I probably won't change it.

Despite the issues, all the games are at least playable.

# Original readme

Genesis Plus GX is an open-source Sega 8/16 bit emulator focused on accuracy and portability. Initially ported and developped on Gamecube / Wii consoles through [libogc / devkitPPC](http://sourceforge.net/projects/devkitpro/), this emulator is now available on many other platforms through various frontends such as:

* [Retroarch (libretro)](http://www.libretro.com)

* [Bizhawk](http://tasvideos.org/Bizhawk.html)

* [OpenEmu](http://openemu.org/)

----

The source code, initially based on Genesis Plus 1.2a by [Charles MacDonald](http://www.techno-junk.org/ ) has been heavily modified & enhanced, with respect to original goals and design, in order to improve emulation accuracy as well as adding support for new peripherals, cartridge or console hardware and many other exciting [features](https://bitbucket.org/eke/genesis-plus-gx/src/master/wiki/Features.md).

The result is that Genesis Plus GX is now more a continuation of the original project than a simple port, providing very accurate emulation and [100% compatibility](https://bitbucket.org/eke/genesis-plus-gx/src/master/wiki/Compatibility.md) with Genesis / Mega Drive, Sega/Mega CD, Master System, Game Gear & SG-1000 released software (including all unlicensed or pirate known dumps), also emulating backwards compatibility modes when available. All the people who contributed (directly or indirectly) to this project are listed on the [Credits](https://bitbucket.org/eke/genesis-plus-gx/src/master/wiki/Credits.md) page.

----

Multi-platform sourcecode (core), which is made available for use under a specific non-commercial [license](https://bitbucket.org/eke/genesis-plus-gx/src/master/LICENSE.txt), is maintained on [Bitbucket](https://bitbucket.org/eke/genesis-plus-gx/src/) / [Github](https://github.com/ekeeke/Genesis-Plus-GX) so that other Genesis Plus ports can benefit of it, as I really wish this emulator becomes a reference for _portable_ and _accurate_ Sega 8/16-bit emulation. If you ported this emulator to other platforms or need help porting it, feel free to contact me.

----

Latest official Gamecube / Wii standalone port (screenshots below) is available [here](https://bitbucket.org/eke/genesis-plus-gx/downloads). Be sure to check the included user manual first. A [startup guide](https://bitbucket.org/eke/genesis-plus-gx/src/master/wiki/Getting%20Started.md) and a [FAQ](https://bitbucket.org/eke/genesis-plus-gx/src/master/wiki/Frequently%20Asked%20Questions.md) are also available.

![MainMenu.png](https://bitbucket.org/repo/7AjE6M/images/3565283297-MainMenu.png)
![menu_load.png](https://bitbucket.org/repo/7AjE6M/images/164055790-menu_load.png)

![RomBrowser.png](https://bitbucket.org/repo/7AjE6M/images/1972035547-RomBrowser.png)
![CtrlMenu.png](https://bitbucket.org/repo/7AjE6M/images/2283464354-CtrlMenu.png)

----

You can also test latest compiled builds for Gamecube / Wii and Retroarch (Windows 32-bit version only) by downloading them from [here](https://bitbucket.org/eke/genesis-plus-gx/src/master/builds/).



----

[![btn_donate_LG.gif](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2966212) If you like this project and want to show your appreciation, Paypal donations are always welcomed.