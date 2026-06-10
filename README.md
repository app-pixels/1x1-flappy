> Part of [**app-pixels.com**](https://www.app-pixels.com) — browse + flash this app at [`/apps/1x1-flappy`](https://www.app-pixels.com/apps/1x1-flappy).

# 1x1-flappy

**1x1 Flappy** · v1.0.3

Multiplication trainer with a flappy-style reward game.

**Hardware:** Waveshare ESP32-S3 1.8" AMOLED Touch

**Tags:** `#kids` `#fun` `#offline`

Practice the 1x1: solve 10 in a row to unlock a quick flappy round. Crash or win — either way, the next round changes theme: Day, Sunset, Rainbow, Night, Storm, Rain, Snow, Candy, Ocean, Space. Make it through level 10 for a big celebration; level resets to 1 every power-on.

## Controls
- Touch keypad - tap digits
- **BOOT** - submit answer (green bar)
- **PWR** - backspace (red bar)
- In flappy mode: tap or **BOOT** to flap, **PWR** to pause

## `setup.txt` keys (all optional)
- `MATH_TABLES` - restrict the question pool to specific tables, e.g. `{2,3,5,10}`. Default = all of 1..10.

## Editing `setup.txt`
The device reads `/setup/setup.txt` from the SD card on boot. [Download a working sample](https://sosbxffigpteqilpgxwn.supabase.co/storage/v1/object/public/app-assets/setup/setup.txt) - covers every app - and edit the keys you need.

Don't want to eject the card? Use the [**USB Stick**](/apps/usb-stick) app (mounts the SD card as a USB drive over USB-C) or the [**Filehub**](/apps/filehub) app (edit over WiFi).

## Build

1. Install [arduino-cli](https://arduino.github.io/arduino-cli/) or Arduino IDE 2.x.
2. Add the ESP32 board package (≥ 3.1.0):

   ```
   arduino-cli core update-index --additional-urls https://espressif.github.io/arduino-esp32/package_esp32_index.json
   arduino-cli core install esp32:esp32 --additional-urls https://espressif.github.io/arduino-esp32/package_esp32_index.json
   ```

3. Install the required Arduino libraries:

   - GFX Library for Arduino (moononournation)
   - XPowersLib (lewishe)

4. Compile and upload:

   ```
   FQBN='esp32:esp32:esp32s3:USBMode=default,CDCOnBoot=cdc,PSRAM=opi,FlashSize=16M,FlashMode=qio,PartitionScheme=app3M_fat9M_16MB,UploadSpeed=921600,LoopCore=1,EventsCore=1'
   arduino-cli compile -b "$FQBN" --build-path /tmp/1x1-flappy_build .
   arduino-cli upload  -b "$FQBN" --input-dir /tmp/1x1-flappy_build -p /dev/ttyACM0 .
   ```

   For browser flashing without a build environment, use the [pre-built binary](https://www.app-pixels.com/apps/1x1-flappy).

## License

MIT — see [LICENSE](LICENSE). Do whatever you want with it.

---

Part of the [app-pixels.com](https://www.app-pixels.com) catalogue · live listing: https://www.app-pixels.com/apps/1x1-flappy
