# CANmeleon ZLG USBCANFD-Compatible Firmware — ZCANPRO, ZXDoc, CANtest and ZLG API

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon ZLG USBCANFD firmware connects supported CANmeleon USB-CAN/CAN FD hardware to ZCANPRO, ZXDoc, CANtest and ZLG API on Windows. This repository provides firmware capabilities, hardware requirements and installation instructions.

[Features and performance](#features-and-performance) · [Download and install](#download-and-install) · [Supported devices](https://canmeleon.com/en/firmware/devices/) · [Firmware catalog](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## Supported hardware

Choose a device listed for **ZLG USBCANFD** in the [CANmeleon device catalog](https://canmeleon.com/en/firmware/devices/). This mode requires 2 / 4 physical CAN channels as applicable, and a license for the selected mode. Connect the device in [CANmeleon Device Manager](https://github.com/CANmeleon/canmeleon-device-manager) to check its exact model and available firmware.

**200U provides two CAN/CAN FD channels; 400U provides four.** Select according to the physical channels and mode license of your device.

<!-- firmware-parameters:start -->
## Features and performance

200U / 400U modes supported; channel count depends on hardware and licensing. Performance and accuracy figures apply to the modes specified in the tables.

### Communication capabilities

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| CAN channels | 200U: 2 channels; 400U: 4 CAN / CAN FD channels | Each channel supports transmission and reception; available modes depend on hardware and licensing. |
| Frame formats | 11 / 29-bit IDs; Classic CAN 0–8 B, CAN FD up to 64 B | Classic RTR supported; CAN FD supports BRS enabled or disabled. |
| Classic CAN bit rate | 5 kbit/s–1 Mbit/s | Configure the bus bit rate in the host software. |
| CAN FD data-phase bit rate | Up to 8 Mbit/s | Configure arbitration and data phases independently; use transceivers and bus wiring suitable for the selected rates. |
| Receive ID filtering | Standard / extended frame ID-range filtering supported; up to 16 rules per channel | Configure before starting communication. |
| Device-side periodic transmission | Up to 16 periodic transmission tasks supported | Total per device; period configuration in 100 µs steps, with start and stop controls. |

### Timestamps

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Hardware receive timestamps | Supported | Read frame reception times through the ZLG API. |
| Hardware transmit-completion timestamps | Supported | Enable transmit echo to read actual transmission completion times. |
| Timestamp resolution (ZLG API) | 1 µs | Received frames and transmit-completion echo frames both have timestamps in 1 µs steps. |

### Software and APIs

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Software | ZCANPRO / ZXDoc / CANtest supported | Install the ZLG driver and select the matching device model. |
| Development API | Windows / ZLG API supported | Use zlgcan.dll for application development. |

<!-- firmware-parameters:end -->

## Download and install

1. Install [CANmeleon Device Manager for Windows x64](https://canmeleon.com/en/device-manager/#downloads), connect the device and check the available firmware.
2. Choose an applicable package in **Firmware Catalog**, or download a complete package from the [GitHub firmware Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases) and use **Import firmware ZIP**. [Gitee releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases) provide the existing download channel. Follow the chosen release's device and manager requirements.
3. Select **ZLG USBCANFD**, review storage and pending changes, and confirm installation. Keep the USB connection and power stable until writing finishes.
4. Reconnect and switch to the installed firmware. Wait for USB re-enumeration.
5. Install the ZLG driver and select USBCANFD-200U or USBCANFD-400U to match the active mode. Use the [driver download page](https://manual.zlg.cn/web/#/146) and the [ZLG USBCANFD setup guide](https://canmeleon.com/en/firmware/zlg-usbcanfd/).
6. Configure each channel for your bus, then verify frame transmission and reception.

[Firmware management](https://canmeleon.com/en/device-manager/firmware-management/) · [Updates and recovery](https://canmeleon.com/en/device-manager/updates-and-recovery/)

## Frequently asked questions

**Which hardware receives this firmware?** Install it on compatible CANmeleon devices selected through the catalog and Device Manager. The mode name identifies the software interface; firmware updates for third-party-manufactured devices come from their manufacturers.

**Does switching firmware add physical channels?** Channel count depends on the hardware and selected mode. A four-channel mode requires four physical CAN channels and its corresponding license.

**Are these figures guaranteed for every workload?** Use the bus rates, frame length, direction, mode and short-duration qualifiers in each row. Configurable data-phase bit rate and typical frame throughput describe different properties.

**Where is the source code?** This repository contains documentation, parameter data and binary-download links. Refer to the component or release for its license.

## Feedback and related resources

Firmware problems and new feature requests can be submitted as [Issues in the CANmeleon firmware main repository](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues). Include the device model, active mode, firmware and driver versions, software/API, bus configuration and steps to reproduce.

[ZLG USBCANFD parameter table](docs/parameters/zlg-usbcanfd.md) · [Parameter JSON (Chinese)](docs/parameters/zlg-usbcanfd.json) · [Device Manager issues](https://github.com/CANmeleon/canmeleon-device-manager/issues)
