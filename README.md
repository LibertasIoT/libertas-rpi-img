# Libertas Hub Raspberry Pi Images

This repository contains the Libertas Hub release for Raspberry Pi 2, Raspberry Pi 3, and Raspberry Pi 4.

## What is Libertas Hub?

Libertas Hub is an IoT central controller with an IoT App design, Thing-App.

Libertas is designed to reach **billions** of users and cover **trillions** of CPU/MCU chips. 

Our goal is to make everything intelligent, not just intelligent in itself but also intelligently interacting with any other things.

Our Thing-App is "write once, run everywhere" across all different CPUs/MCUs from inside tiny sensors to the big Cloud. In other words, Thing-App **interconnects** different things and defines **interaction** among them, while those things could be otherwise seemingly unrelated without Thing-App.

Libertas Thing-App is right at your fingertips. An end-user chooses a Thing-App, throws things into the Thing-App, then starts the Thing-App. Libertas will figure out how to interconnect related "things" around the Thing-App, and find the best place (e.g., a little sensor, Hub or Cloud) for Thing-App to run securely and privately.

After ten years of research & development, Libertas Hub now reached production-ready quality. We will [open source the complete code for MCUs](https://librehome.com/doc/hornet_doc/) soon, although it may take a little more time. We cannot wait to release the Hub for curious people to try out.

With its simple yet disruptive design, I am confident Libertas will lead in the following decades.

## Prepare the hardware.

You will need:
1. A Raspberry Pi 2, 3, or 4 board.
2. A microSD card as main storage. A size of >= 16GB is recommended; 8 GB is the minimum.
3. A [nRF52840 Dongle](https://www.nordicsemi.com/Products/Development-hardware/nrf52840-dongle). It costs about USD 10.
4. A USB thumb drive as backup storage. The Hub must have dual storage backup. Also, the thumb drive is IoT data storage.

<img src="images/rpi_comp.png" width="480" />

## Download the zip file and extract

Get the zip file for your Raspberry Pi model from the [latest release (https://github.com/LibertasIoT/libertas-rpi-img/releases)](https://github.com/LibertasIoT/libertas-rpi-img/releases) and extract the zip file.

## Prepare the nRF52840 Dongle

The nRF52840 Dongle is required as a radio transceiver. Use the nRF tool below to program Hornet transceiver firmware into the Dongle.

### Download nRF Connect Desktop

Follow this link ([https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop](https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-desktop)). 

The download link is on the left side of the webpage.

Install the software. Then launch the software. Note that we only need the "programmer App," as shown in the screenshot below.

<img src="images/nrfConnect.png" width="480" />

### Program transceiver firmware

#### Use the NRF programmer

First, click the "Add file" button in the upper left part of the window. Choose the .img file that comes with the zip file. The file name should be:

**```nrf52840-transceiver.img.hex```**

The plug dongle into the USB port of the machine. Wait for a few seconds. There should be a "USB plug-in sound" on the Windows platform. Then choose the Dongle from the "SELECT DEVICE" button on the uppermost left side.

The correct device shall be an "Open DFU bootloader."

As the last step, click the "write" button on the left, and wait for the writing progress to finish.

Unplug the Dongle and plug it into a USB port of the Raspberry Pi. It is OK to use a USB 1.1 or 2.0 port.

There is a button on the Dongle. Please ensure you can still access the button while the Dongle is plugged into the Raspberry Pi. During Hub admin processes, you may be asked to press the button to prove that you have physical access to the Hub.

<img src="images/nrfProgrammer.png" width="480" />

## Prepare the microSD card

It is recommended to use Rufus to write to a microSD card. You can download Rufus from [https://rufus.ie/](https://rufus.ie/).

Choose the microSD card and the Raspberry Pi image. Leave all other parameters with their default values and click START to initiate the writing process. The image file shall be something like the below,

**``` libertas-raspberrypiN_2022XXXXXXXXXX_fullsd.img ```**

![rufus](images/rufus.png)

Two warning dialogs may pop up. 

Press "OK" on each dialog to proceed.

<img src="images/rufus.warn1.png" width="240" /> <img src="images/rufus.warn2.png" width="240" />

## Setup the Hub

Once Rufus is done writing the micro SD card. Remove the card from the PC and plug it into your Raspberry Pi.

Make sure the nRF52840 Dongle and USB drive are also plugged in. Then power on the Raspberry Pi.

Follow this instruction to set up the Hub using Libertas Android App.

[https://librehome.com/doc/smartphone_app/managing_hubs/add_a_new_hub/](https://librehome.com/doc/smartphone_app/managing_hubs/add_a_new_hub/)

Note that Raspberry Pi Hub will not be able to use our bridge service. Instead, you will need to set up the dynamic DNS and NAT to access the Hub from the Internet through our Libertas Smartphone App.

## What Can I do With the Libertas Hub?

The Libertas Hub currently supports Hornet Mesh wireless technology. In addition, it works with [9 Libertas smart home devices](https://librehome.com) now.

What about Google's Thread and Matter technology? Well, since Matter is IP based. The Hub can support it right now. Nevertheless, for now, in Libertas, Matter is just a Thing-App!

Native matter support is part of a bigger Libertas plan. We want every device to have a Thing-App virtual machine and to interact with other devices independently, securely, and privately. Moreover, the underlying wireless protocol shall be transparent. Which is Hornet OS for MCU with Hornet Cluster Library that we are working to open source now.

[As for Hornet, why another mesh network technology? Can Hornet even survive? Here are my thoughts.](https://librehome.com/doc/hornet_doc/index.html#why-another-mesh-protocol)

Libertas is many years ahead. We laid the foundation of both interconnectivity and interactivity. It is more about the IoT intelligence layer than simple connectivity. Plus, when they say "connectivity," it does not necessarily mean **inter**connectivity!

The innovation of Libertas is Thing-App, the application for IoT. We can mathematically prove that Libertas' design brings optimal experience to end-users and application developers.

For end-users, the design is simple three steps. 1. Choose a Thing-App from our Thing-App store; 2. Throw things into the Thing-App, possibly with some extra parameters; 3. Start the Thing-App.

![Thing-App](images/appengine.png)

For developers, the design can not be more straightforward. First, the developer decides what type of things and extra parameters are needed for their Thing-App. The developer must then design a tree structure for those things and parameters. Next, the developer declares the tree structure as a few classes in the source code. At last, the developer writes a function as a process with necessary arguments.

The Libertas IDE (web-based builtin with the Hub) will analyze type declarations in source code and automatically generate the UI on a smartphone for a user to create the tree data based on the type declarations.

![Tree UI](images/tree_ui.png)

![Libertas Studio](images/libertas_studio.png)

### Additional technical documentations

Follow the link below to read the technical overview slides.

[https://docs.google.com/presentation/d/1oxe2K6-h2BWhlbm56ZZ4ZNBXoStRQs_iNyDqhWXge3w](https://docs.google.com/presentation/d/1oxe2K6-h2BWhlbm56ZZ4ZNBXoStRQs_iNyDqhWXge3w).

Follow the link below to read the developer guides.

[https://librehome.com/doc/developers_doc](https://librehome.com/doc/developers_doc)

Follow the link below for the latest up-to-date API documentation.

[librehome.com/api/modules/libertas.html](librehome.com/api/modules/libertas.html)

Libertas is a general-purpose IoT platform with two operating systems, not just for smart homes!

### Tutorials

While we will open-source the complete code for MCUs later,  there is plenty you can do with Libertas Hub. For example, you can start experimenting with App development, go through the tutorial code, and code for existing Apps, such as "Demon A/V receiver driver."

![tutorials](images/libertas_tutorials.png)

### Denon/Marantz A/V receiver driver

Another smart home example one can look at is the Denon/Marantz A/V receiver driver App. The end-user throws a receiver into the App during configuration (automatically discovered in the local network if it exists), and several "virtual devices" will be automatically created.

End users can control their receivers using our standard UI with our smartphone App. A few clicks can bind the controls to real buttons such as Libertas remote control. Furthermore, those virtual devices can be controlled with other Apps just like real devices.

It works much better than the official App on your smartphone! [Here is the source code](https://github.com/librehome/librehome/blob/main/SmartonLabs/LibertasDenonAVR.ts) if you don't want to try Hub for now.

![Virtual Device](images/virtual_device.png)

## Commercialization

Current versions of Libertas Hub are free for individuals. However, we plan a license charge starting from a future release.

Whatever the plan is, it is going to be simple. Libertas end-users shall enjoy total control, zero information leaks, and be free from stealing, robbing, and Ponzi Schemes.

![](images/cp1.png) ![](images/cp4.png) 

<img src="images/cp3.gif" width="150" /> <img src="images/cp7.gif" height="150" /> ![](images/cp2.png) ![](images/cp8.png)

![](images/cp5.png) ![](images/cp6.png) 
