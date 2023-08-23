---
title: Getting started with Google OpenSK
date: 2020-02-09
authors:
  - makerdiary
cover: getting-started-with-google-opensk/cover.png
categories:
  - Learn
description: >
  This post details how to get started with the OpenSK using the nRF52840 MDK USB Dongle without going through the complete toolchain installation.
---

![](cover.png)

# Getting started with Google OpenSK

## Introduction

[OpenSK](https://github.com/google/OpenSK) released by Google is a fully open-source implementation for security keys written in Rust that supports both FIDO U2F and FIDO2 standards.

OpenSK is based on the FIDO2 specifications, which combine the World Wide Web Consortium’s (W3C) [Web Authentication (WebAuthn)](https://fidoalliance.org/fido2/fido2-web-authentication-webauthn/) specification and FIDO Alliance’s corresponding [Client-to-Authenticator Protocol (CTAP)](https://fidoalliance.org/specifications/download/).

The nRF52840 MDK USB Dongle works well with OpenSK. Taking advantage of the UF2 Bootloader, you can easily program the OpenSK by just copying the `.uf2`-format image to the flash drive.

This guide details how to get started with the OpenSK using the nRF52840 MDK USB Dongle without going through the complete toolchain installation.

## Requirements

Before you start, check that you have the required hardware and software:

- 1x [nRF52840 MDK USB Dongle](https://makerdiary.com/products/nrf52840-mdk-usb-dongle)(or [w/Case](https://makerdiary.com/products/nrf52840-mdk-usb-dongle-w-case) option)
- Latest version of Google Chrome, Mozilla Firefox, Microsoft Edge or Apple Safari

## Programming the latest OpenSK firmware

Download the [latest firmware](https://github.com/makerdiary/OpenSK-firmware/releases) and complete the following steps to program the firmware:

1. Push and hold the button and plug your dongle into the USB port of your computer. Release the button after your dongle is connected. The RGB LED turns green.
2. It will mount as a Mass Storage Device called __UF2BOOT__.
3. Drag and drop `opensk-nrf52840_mdk_usb_dongle-<version>.uf2` onto the __UF2BOOT__ volume. The RGB LED blinks red fast during flashing.
4. Re-plug the dongle and the OpenSK device will start running.

!!! Note "About the Volume Label"

    The dongle manufactured after July 20 2023 is shipped with the latest [UF2 Bootloader 0.7.1](https://github.com/makerdiary/nrf52840-mdk-usb-dongle/tree/main/firmware/uf2_bootloader), which will mount as a Mass Storage Device called __UF2BOOT__. If you are running the older bootloader, it will mount as __MDK-DONGLE__.

## Testing OpenSK

After flashing the firmware to your dongle, complete the following steps to test it:

1. Visit https://webauthn.io/ in a supported web browser, for example, Google Chrome.
2. Enter an example username and then click __Register__. You will be prompted to choose the way to create a passkey. Select __USB security key__.
    ![](choose-webAuthn-way.png)

3. Plug the dongle into the USB port of your computer. __Red LED__ and __Blue LED__ are blinking, which asks you to confirm the transaction with a button press.

4. After the button is pressed, you will be prompted to enter a PIN for your security key. Just enter your PIN and click __Next__.
    ![](webAuthn-PIN-required.png)


5. __Red LED__ and __Blue LED__ are blinking again and press the button again to complete the request. Then you will see the success notification.
    ![](webAuthn-register-success.png)

6. Now try to authenticate by click __Authenticate__. You will be prompted to enter the PIN you set above. Just enter your PIN and click __Next__.
    ![](enter-pin-authentication.png)

7. __Red LED__ and __Blue LED__ are blinking and you are asked to confirm the request with a button press. Press the button and you will be logged in.
    ![](webAuthn-logged-in.png)

## Explore More

The two-factor authentication (2FA) has been successfully deployed by a growing number of websites and platforms, including Google, social networks, cloud providers, and many others. Happy trying!
