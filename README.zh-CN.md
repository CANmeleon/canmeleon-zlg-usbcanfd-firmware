# CANmeleon ZLG USBCANFD 兼容固件 — ZCANPRO、ZXDoc、CANtest 与 ZLG API

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon ZLG USBCANFD 固件让适用的 CANmeleon USB-CAN/CAN FD 硬件在 Windows 上接入 ZCANPRO、ZXDoc、CANtest 与 ZLG API。本仓库提供固件能力、硬件要求及安装说明。

[固件特性与性能参数](#固件特性与性能参数) · [下载与安装](#下载与安装) · [支持设备](https://canmeleon.com/zh/firmware/devices/) · [固件总览](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## 支持硬件

在 [CANmeleon 设备目录](https://canmeleon.com/zh/firmware/devices/)选择支持 **ZLG USBCANFD** 的硬件。按所选模式配备 2 / 4 路物理 CAN 接口及对应授权。连接[设备管理器](https://github.com/CANmeleon/canmeleon-device-manager)核对完整型号及可安装固件。

**200U 提供双通道 CAN/CAN FD，400U 提供四通道。** 按实际物理通道和模式授权选择。

<!-- firmware-parameters:start -->
## 固件特性与性能参数

支持 200U / 400U 模式；通道数按硬件与授权选择，性能与精度按表中标注的模式使用。

### 通信能力

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| CAN 通道 | 200U：2 路；400U：4 路 CAN / CAN FD | 每通道支持发送和接收；可用模式取决于硬件和授权。 |
| 报文格式 | 11 / 29 位 ID；Classic CAN 0–8 B，CAN FD 最高 64 B | 支持 Classic RTR；CAN FD 支持 BRS 开启 / 关闭。 |
| Classic CAN 速率 | 5 kbit/s–1 Mbit/s | 通过上位机设置总线速率。 |
| CAN FD 数据速率 | 最高 8 Mbit/s | 仲裁段与数据段独立配置；需配套支持相应速率的收发器和总线布线。 |
| 接收 ID 过滤 | 支持标准帧 / 扩展帧 ID 范围过滤；每通道最多 16 条 | 建议在开始通信前配置。 |
| 设备定时发送 | 支持最多 16 项定时发送任务 | 设备合计；周期设置步进 100 µs，支持启动和停止。 |

### 时间戳

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 接收硬件时间戳 | 支持 | 通过 ZLG API 读取报文接收时间。 |
| 发送完成硬件时间戳 | 支持 | 开启发送回显后读取实际发送完成时间。 |
| 时间戳分辨率（ZLG API） | 1 µs | 接收报文和发送完成回显的时间戳均以 1 µs 为步进。 |

### 软件配套

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 配套软件 | 支持 ZCANPRO / ZXDoc / CANtest | 安装 ZLG 驱动，选择对应设备型号。 |
| 开发接口 | 支持 Windows / ZLG API | 使用 zlgcan.dll 进行二次开发。 |

<!-- firmware-parameters:end -->

## 下载与安装

1. 安装 [Windows x64 设备管理器](https://canmeleon.com/zh/device-manager/#downloads)，连接设备并检查适用固件。
2. 从固件目录选择适用包，或从 [GitHub 固件 Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases)下载完整包并使用“导入固件 ZIP”。已有下载渠道见 [Gitee Releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases)。按所选版本说明核对设备及管理器要求。
3. 选择 **ZLG USBCANFD**，检查空间和待执行变更，确认安装；保持 USB 连接和供电稳定直至写入完成。
4. 重新连接并切换到所安装的固件，等待 USB 重新识别。
5. 安装 ZLG 驱动，按当前固件模式选择 USBCANFD-200U 或 USBCANFD-400U。 参阅[驱动下载页](https://manual.zlg.cn/web/#/146)及 [ZLG USBCANFD 配置指南](https://canmeleon.com/zh/firmware/zlg-usbcanfd/)。
6. 按总线配置设置各通道，确认能够正常发送和接收报文。

[固件管理](https://canmeleon.com/zh/device-manager/firmware-management/) · [更新与恢复](https://canmeleon.com/zh/device-manager/updates-and-recovery/)

## 常见问题

**固件安装到什么硬件？** 安装于设备目录和管理器列出的适用 CANmeleon 硬件。模式名称表示软件接口；第三方原厂硬件的升级固件由对应厂商提供。

**切换固件能增加物理通道吗？** 通道数由硬件和所选模式决定。四通道模式需要四路物理 CAN 接口及对应授权。

**性能数据适用于所有工况吗？** 按各行的速率、帧长、方向、模式和短时限定使用。可配置的数据段速率与典型报文吞吐是不同指标。

**固件源码在哪里？** 本仓库提供文档、参数数据和二进制下载入口，许可信息以对应组件或发布包为准。

## 问题与新需求反馈

固件相关的问题和新需求可在 [GitHub 固件主仓库提 Issue](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues)。请附设备型号、当前模式、固件与驱动版本、软件/API、总线配置及复现步骤。

[ZLG USBCANFD 参数表](docs/parameters/zlg-usbcanfd.zh-CN.md) · [参数 JSON](docs/parameters/zlg-usbcanfd.json) · [设备管理器问题](https://github.com/CANmeleon/canmeleon-device-manager/issues)
