# CANmeleon ZLG USBCANFD Firmware Features and Performance

200U / 400U modes supported; channel count depends on hardware and licensing. Performance and accuracy figures apply to the modes specified in the tables.

## Communication capabilities

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| CAN channels | 200U: 2 channels; 400U: 4 CAN / CAN FD channels | Each channel supports transmission and reception; available modes depend on hardware and licensing. |
| Frame formats | 11 / 29-bit IDs; Classic CAN 0–8 B, CAN FD up to 64 B | Classic RTR supported; CAN FD supports BRS enabled or disabled. |
| Classic CAN bit rate | 5 kbit/s–1 Mbit/s | Configure the bus bit rate in the host software. |
| CAN FD data-phase bit rate | Up to 8 Mbit/s | Configure arbitration and data phases independently; use transceivers and bus wiring suitable for the selected rates. |
| Receive ID filtering | Standard / extended frame ID-range filtering supported; up to 16 rules per channel | Configure before starting communication. |
| Device-side periodic transmission | Up to 16 periodic transmission tasks supported | Total per device; period configuration in 100 µs steps, with start and stop controls. |

## Timestamps

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Hardware receive timestamps | Supported | Read frame reception times through the ZLG API. |
| Hardware transmit-completion timestamps | Supported | Enable transmit echo to read actual transmission completion times. |
| Timestamp resolution (ZLG API) | 1 µs | Received frames and transmit-completion echo frames both have timestamps in 1 µs steps. |

## Software and APIs

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Software | ZCANPRO / ZXDoc / CANtest supported | Install the ZLG driver and select the matching device model. |
| Development API | Windows / ZLG API supported | Use zlgcan.dll for application development. |
