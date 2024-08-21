# Upgrade Sonoff coordinator firmware
Follow instructions given here: https://sonoff.tech/wp-content/uploads/2021/12/SONOFF-Zigbee-3.0-USB-dongle-plus-firmware-flashing-1-1.pdf

TL;DR:
- download firmware image: https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/bin/CC1352P2_CC2652P_launchpad_coordinator_20230507.zip
- unzip [firmware image](CC1352P2_CC2652P_launchpad_coordinator_20230507.hex)
- flash firmware via docker 1-liner: https://github.com/git-developer/ti-cc-tool/tree/main?tab=readme-ov-file#docker-compose
- flash firmware manually:
  - install requirements:
  ```
  pip3 install wheel pyserial intelhex python-magic
  ```
  - identify your usb dongle interface:
  ```
  ls -la /dev/serial/by-id/
  
  lrwxrwxrwx 1 root root 13 Aug 20 23:53 usb-Silicon_Labs_Sonoff_Zigbee_3.0_USB_Dongle_Plus_0001-if00-port0 -> ../../ttyUSB0
  ```
  - run:
  ```
  python3 cc2538-bsl.py -p /dev/serial/by-id/usb-Silicon_Labs_Sonoff_Zigbee_3.0_USB_Dongle_Plus_0001-if00-port0 -e -v -w --bootloader-sonoff-usb CC1352P2_CC2652P_launchpad_coordinator_20230507.hex
  ```
