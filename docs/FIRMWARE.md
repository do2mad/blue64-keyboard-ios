# Firmware

The app needs the BT-64 firmware with the **BLE keyboard service**.

## Status

The extension has been proposed to the BT-64 project
([sideprojectslab/BT-64](https://github.com/sideprojectslab/BT-64)).
Until it is part of an official release, use the firmware from the fork
[do2mad/BT-64](https://github.com/do2mad/BT-64) (branch `ble-keyboard`).

## Install

1. Copy `application.bin` to the root of a FAT-formatted SD card.
2. Insert the card into the BT-64 and switch the C64 on.
3. The BT-64 types *"firmware update started!"* on the screen and reports success after about a minute.
   Switch the C64 off and remove the card.

**Going back:** put the official `application.bin` from the BT-64 releases on the SD card
and repeat the steps. The update routine and the bootloader are not changed by the extension.

## Build it yourself

ESP-IDF **5.5.4** is required.

```sh
git clone --recursive https://github.com/do2mad/BT-64
cd BT-64
git checkout ble-keyboard

# BTstack patch recommended by Bluepad32, then integrate BTstack
cd ext/bluepad32/external/btstack
git apply ../patches/*.patch
cd port/esp32
IDF_PATH=$PWD/../../../../../../dev/sw/src python3 integrate_btstack.py

# build
cd ../../../../../../dev/sw
. ~/esp/esp-idf/export.sh
idf.py -B _make/work -C src build    # -> _make/work/application.bin
```

The project's own `inv` build script does the same and expects the environment variable
`ESP_IDF_5_5_4` (see the BT-64 README).
