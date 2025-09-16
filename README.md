# Libertas Hub Raspberry Pi Images, Technical Preview

Powered by [Thing-App](https://docs.smartonlabs.com/developers_doc/libertas_thing_app/) on [Libertas OS](https://docs.smartonlabs.com/developers_doc/libertas_os/)

## This product is *not certified with any standard body, including but not limited to Matter and Thread*. The product shall not be used for any production purpose. It shall only be used to evaluate the Smartonlabs technology.

## What is Libertas Hub?

Read [Smartonlabs Libertas IoT product tour](https://smartonlabs.com).

## Prepare the hardware.

You will need:
1. A Raspberry Pi 2, 3, 4 or 5 board.
2. A microSD card as main storage. A size of 32 GB or greater is recommended; 16 GB is the minimum.
3. A USB Radio Co-processor (RCP). It can be [ESP32-C6](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32c6/esp32-c6-devkitc-1/user_guide.html#hardware-reference), or [ESP32-H2](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32h2/esp32-h2-devkitm-1/user_guide.html), or [ESP32-C5](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32c5/esp32-c5-devkitc-1/user_guide.html#hardware-reference), or [nRF52840 Dongle](https://www.nordicsemi.com/Products/Development-hardware/nrf52840-dongle), or [XIAO MG24](https://www.seeedstudio.com/Seeed-Studio-XIAO-MG24-p-6247.html). It costs about USD 10.
4. A USB drive (thumb or SSD) as backup storage. **The Hub must have dual storage backup**. Additionally, the USB drive serves as a storage device for IoT data.

USB drive shall be plugged in a faster USB port (blue, not black port). RF dongle shall be away from the ethernet port.

A high speed USB drive (or NVMe USB 3 adapter for RPi 4&5) is recommended. I've experienced a [really bad Amazon basic drive](https://www.amazon.com/dp/B0B61DGG18) with only 10MB write speed.

<img src="images/rpi_comp.png" width="480" />

## Download the ZST file and extract

Get the zst file for your Raspberry Pi model from the [latest release (https://github.com/LibertasIoT/libertas-rpi-img/releases)](https://github.com/LibertasIoT/libertas-rpi-img/releases) and extract the zst file (Zstd compression).

## Prepare USB Radio Co-processor (RCP)

### ESP32 development kits

You need to compile and flash the firmware. Read [this link](https://github.com/espressif/esp-idf/blob/master/examples/openthread/ot_rcp/README.md) for more details.

<img src="images/esp32-h2-dev-kit.webp" width="320" />

### XIAO MG24

Follow the link [https://github.com/SiliconLabs/arduino](https://github.com/SiliconLabs/arduino) for MCP firmware.

<img src="images/XIAO_MG24.webp" width="240" />

### nRF52840 dongle

The compiled firmware image can be downloaded from [release section](https://github.com/LibertasIoT/libertas-rpi-img/releases). Use the nRF tool below to program the firmware into the dongle.

You can also compile your own firmware by following [this link](https://docs.nordicsemi.com/bundle/ncs-latest/page/nrf/protocols/thread/tools.html#configuring-a-radio-co-processor).

#### Download nRF Connect Desktop

Follow this link ([https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop](https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop)). 

The download link is on the left side of the webpage.

Install the software. Then, launch the software. Note that we only need the "programmer App," as shown in the screenshot below.

<img src="images/nrfConnect.png" width="480" />

#### Use the NRF programmer

First, click the "Add file" button in the upper left part of the window. Next, select the .img file included in the zip file. The file name should be:

**```nrf52840_rcp_20250402.hex```**

Then, plug the dongle into the USB port of the machine. Wait for a few seconds. There should be a "USB plug-in sound" on the Windows platform. 

Press the "reset button" on the dongle. The button press shall be horizontal to the PCB board, as shown in the picture below. The dongle shall be in programming mode.

<img src="images/nrf52840_dongle_prog.png" />

Then, choose the dongle from the "SELECT DEVICE" button located on the upper left side.

The correct device shall be an "Open DFU bootloader."

As the final step, click the "Write" button on the left and wait for the writing progress to complete.

Make sure the write operation is successful.

Unplug the dongle and plug it into a USB port of the Raspberry Pi.

<img src="images/nrfProgrammer.png" width="480" />

## Prepare the microSD card

The image file is compressed with zstd. The extracted file name is something like the below:

**```libertas-raspberrypi?_2025??????????_fullsd.wic```**

### Linux users

Linux users can [use the **dd** command to write to an SD card](https://askubuntu.com/questions/227924/sd-card-cloning-using-the-dd-command).

### Windows users

It is recommended to use Rufus to write to a microSD card. You can download Rufus from [https://rufus.ie/](https://rufus.ie/).

Choose the microSD card and the Raspberry Pi image. Leave all other parameters with their default values and click START to initiate the writing process.

**```libertas-raspberrypi??_2025??????????_fullsd.wic```**

![rufus](images/rufus.png)

Two warning dialogs may pop up. 

Press "OK" on each dialog to proceed.

<img src="images/rufus.warn1.png" width="240" /> <img src="images/rufus.warn2.png" width="240" />

Once Rufus is done writing the micro SD card. Remove the card from the PC and plug it into your Raspberry Pi. 

## Prepare a USB drive

Format a single partition with **exFat**.

*Note: The USB drive will be automatically **reformated** into ext4 by Hub during the first startup. All content on the drive will be lost!!!*

## Power up the Pi

**Ensure the nRF52840 Dongle and USB drive are plugged in before powering up your Pi.**

**Also, ensure the Hub's ethernet port is plugged into the local network.**

## Smartphone App

The iOS App is always 10% behind, and it has not been released yet.

Follow the links below to download the Android App. Or download android APK from the [release page](https://github.com/LibertasIoT/libertas-rpi-img/releases).

<a href="https://play.google.com/store/apps/details?id=com.smartonlabs.qwha"><img src="images/badge_new.png" width="135" /></a>

## Setup the Hub

Follow these instructions to set up the Hub using the Libertas Android App.

[https://docs.smartonlabs.com/smartphone_app/managing_hubs/add_a_new_hub/](https://docs.smartonlabs.com/smartphone_app/managing_hubs/add_a_new_hub/)

Powering up the Hub for the first time takes longer than usual because of the extra initialization steps, such as expanding and formatting the data partition on the SD card.

The service also takes minutes to get ready due to the dependencies [explained below](#startup-reboot-wait-time).

Keep the "[Discovery](https://docs.smartonlabs.com/smartphone_app/managing_hubs/add_a_new_hub/#search-local-network-for-hubs)" screen open, and the Hub will appear as soon as it's ready.

Please note that the Raspberry Pi Hub will not be able to utilize our bridge service. Instead, you will need to set up the dynamic DNS and NAT to [access the Hub](https://docs.smartonlabs.com/smartphone_app/managing_hubs/hub_connection_settings/#using-static-ip) from the Internet through our Libertas Smartphone App.

### Current builds

Raspberry 2, 3, 4, and 5 images built with the latest Yocto LTS Scarthgap.

- A/B partition upgrade
- USB drive backup
- Latest Linux 6.12 kernel
- Built-in OpenThread Border Router (OTBR)
- ARM32 (Raspberry Pi 2, 3, and 4) and ARM64 (Raspberry Pi 5) builds

Raspberry Pi 5 NVMe boot

The Raspberry Pi 5 image is GPT based instead of MBR. The same image works with both SD card and NVMe. Note the following:

- Use Raspberry Pi OS to update the latest firmware is recommended (even if you use SD card)
- Libertas Hub will automatically change the PARTUUID of the rootfs after the first boot

## Access Libertas IoT Studio IDE

[Every Libertas IoT Hub comes with Libertas-IoT Studio, a complete development IDE that is free for everybody.](https://docs.smartonlabs.com/developers_doc/development_tool/)

![Libertas Studio](images/libertas_studio.png)

## Startup/Reboot wait time

The Libertas service takes about 1-2 minutes to go back online because it depends on too many services such as chronyd (see below). So please be patient.

Last updated: 2025-09-13
