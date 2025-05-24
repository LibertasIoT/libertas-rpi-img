# Libertas Hub Raspberry Pi Images<br/>
Powered by [Libertas OS](https://docs.smartonlabs.com/developers_doc/libertas_os/)

## What is Libertas Hub?

Read the following documents:

- [Libertas Thing-App](https://docs.smartonlabs.com/developers_doc/libertas_thing_app/)
- [Libertas Hub](https://docs.smartonlabs.com/developers_doc/libertas_hub/)

## Prepare the hardware.

You will need:
1. A Raspberry Pi 2, 3, or 4 board.
2. A microSD card as main storage. A size of >= 16GB is recommended; 8 GB is the minimum.
3. A [nRF52840 Dongle](https://www.nordicsemi.com/Products/Development-hardware/nrf52840-dongle). It costs about USD 10.
4. A USB thumb drive as backup storage. The Hub must have dual storage backup. Also, the thumb drive is IoT data storage.

<img src="images/rpi_comp.png" width="480" />

## Download the zip file and extract

Get the zip file for your Raspberry Pi model from the [latest release (https://github.com/LibertasIoT/libertas-rpi-img/releases)](https://github.com/LibertasIoT/libertas-rpi-img/releases) and extract the zip file.

## Prepare the nRF52840 dongle

The nRF52840 Dongle is required as a radio transceiver. Use the nRF tool below to program Hornet transceiver firmware into the dongle.

Note other dongle hardware also work, e.g., [ESP32-S2](https://docs.espressif.com/projects/esp-idf/en/stable/esp32s2/api-guides/openthread.html). Check the vendor documentation about building and flashing.

### Download nRF Connect Desktop

Follow this link ([https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop](https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop)). 

The download link is on the left side of the webpage.

Install the software. Then launch the software. Note that we only need the "programmer App," as shown in the screenshot below.

<img src="images/nrfConnect.png" width="480" />

### Program RCP firmware

#### Use the NRF programmer

First, click the "Add file" button in the upper left part of the window. Next, choose the .img file that comes with the zip file. The file name should be:

**```nrf52840_rcp_20250402.hex```**

Then plug the dongle into the USB port of the machine. Wait for a few seconds. There should be a "USB plug-in sound" on the Windows platform. 

Press the "reset button" on the dongle. The button press shall be horizontal to the PCB board, as shown in the picture below. The dongle shall be in programming mode.

<img src="images/nrf52840_dongle_prog.png" />

Then choose the dongle from the "SELECT DEVICE" button on the uppermost left side.

The correct device shall be an "Open DFU bootloader."

As the last step, click the "write" button on the left, and wait for the writing progress to finish.

A windows will popup to notify that the write is successful.

Unplug the dongle and plug it into a USB port of the Raspberry Pi. It is OK to use a USB 1.1 or 2.0 port.

<img src="images/nrfProgrammer.png" width="480" />

## Prepare the microSD card

It is recommended to use Rufus to write to a microSD card. You can download Rufus from [https://rufus.ie/](https://rufus.ie/).

We have taken the public download off line. Contact [founder, Mr. Qingjun,](https://www.linkedin.com/in/qingjunwei/) for the latest image of the Libertas Hub.

Choose the microSD card and the Raspberry Pi image. Leave all other parameters with their default values and click START to initiate the writing process. The image file shall be something like the below,

**``` libertas-raspberrypiN_2022XXXXXXXXXX_fullsd.img ```**

![rufus](images/rufus.png)

Two warning dialogs may pop up. 

Press "OK" on each dialog to proceed.

<img src="images/rufus.warn1.png" width="240" /> <img src="images/rufus.warn2.png" width="240" />

Once Rufus is done writing the micro SD card. Remove the card from the PC and plug it into your Raspberry Pi. 

Make sure the nRF52840 Dongle and USB drive are also plugged in. Then power up your Pi.

## Smartphone App

iOS App is always 10% behind and it is not released yet.

Follow the linkes below to download Android App.

<a href="https://play.google.com/store/apps/details?id=com.smartonlabs.qwha"><img src="images/badge_new.png" width="135" /></a>

<a href="amzn://apps/android?asin=B085XQBZN1"><img src="images/amazon-appstore-badge-english-black.png" width="135" /></a>

<a href="https://librehome.com/app-release.apk"><img src="images/apk_badge.png" width="135" /></a>

## Setup the Hub

There is a button on the dongle. Please ensure you can still access the button while the dongle is plugged into the Raspberry Pi. During Hub admin processes, you may be asked to press the button to prove that you have physical access to the Hub.

Follow this instruction to set up the Hub using Libertas Android App.

[https://docs.smartonlabs.com/smartphone_app/managing_hubs/add_a_new_hub/](https://docs.smartonlabs.com/smartphone_app/managing_hubs/add_a_new_hub/)

Note that Raspberry Pi Hub will not be able to use our bridge service. Instead, you will need to set up the dynamic DNS and NAT to access the Hub from the Internet through our Libertas Smartphone App.

## Access Libertas IoT Studio IDE

[Every Libertas IoT Hub comes with Libertas-IoT Studio, a complete development IDE that is free for everybody.](https://docs.smartonlabs.com/developers_doc/development_tool/)

![Libertas Studio](images/libertas_studio.png)

