---
description: Automatic updater to v2.0.0
---

# Comet

### Usage

1. Download the latest Comet jar and a start file (`.bat` for Windows or `.sh` for Linux/MacOS) from [here](https://ci.codemc.io/job/iGabyTM/job/ArcaneVouchers/)
2. Place the files in a folder with the files you want to update (`config.yml`, `vouchers.yml` and `limits.yml`) or to convert
3. Open the start file and add the following flags at the end of the command, depending on what you want to do:
   1. To update: `--action update`
   2. To convert: `--action convert --plugin <plugin>`
4. Save the file and execute it (double-click on Windows/MacOs or `./start.sh` on Linux)

#### Notes for conversion

For [Vouchers by BadBones](https://www.spigotmc.org/resources/vouchers.13654/), add `Config.yml`

For [EpicVouchers by Songoda](https://songoda.com/marketplace/product/epicvouchers-advanced-vouchers-by-gui.25), rename its `vouchers.yml` file to `EpicVouchers.yml`

### Flags

`-h, --help` Display the help menu\
`-a,--action <action>` Available actions: convert, update\
`-p,--plugin <plugin>` Available plugins for conversion: [badbones](https://www.spigotmc.org/resources/vouchers.13654/), [songoda](https://songoda.com/marketplace/product/epicvouchers-advanced-vouchers-by-gui.25)
