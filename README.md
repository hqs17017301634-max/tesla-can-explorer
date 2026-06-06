# Tesla CAN Explorer

Tesla CAN Explorer 是一个开源研究门户，用于浏览已解码的 Tesla CAN 报文、信号和枚举值映射。

本研究项目开源发布在 [GitHub](https://github.com/mikegapinski/tesla-can-explorer)，并由 [Tesla Android](https://teslaandroid.com/) 赞助。想在 Tesla 车机中运行 Android 应用，可访问 [teslaandroid.com](https://teslaandroid.com/)。

独立项目声明：本项目与 Tesla, Inc. 无关联，也未获得 Tesla, Inc. 背书或认可。

## 数据集范围

- 车辆：`Model 3`
- 固件版本：`2026.2`
- 数据来源：`libQtCarCANData.so`、`libQtCarVAPI.so`
- `MCU2 (Intel)` 版本：`./data/can_frames_decoded_all_values_mcu2.json`
- `MCU3 (AMD)` 版本：`./data/can_frames_decoded_all_values_mcu3.json`
- `Model S/X AMD` 版本：`./data/can_frames_decoded_all_values_modelsx_amd.json`
- `Model S/X Intel` 版本：`./data/can_frames_decoded_all_values_modelsx_intel.json`

相关 VAPI 数据：

- `./data/vapi_can_digest.json`
- `./data/vapi_eth_signal_aliases.csv`
- `./data/vapi_can_digest_mcu2.json`
- `./data/vapi_eth_signal_aliases_mcu2.csv`
- `./data/vapi_can_digest_mcu3.json`
- `./data/vapi_eth_signal_aliases_mcu3.csv`
- `./data/vapi_can_digest_modelsx_amd.json`
- `./data/vapi_eth_signal_aliases_modelsx_amd.csv`
- `./data/vapi_can_digest_modelsx_intel.json`
- `./data/vapi_eth_signal_aliases_modelsx_intel.csv`

## 本地运行

在仓库根目录执行：

```bash
python3 -m http.server 8080
```

然后在浏览器打开：

- `http://localhost:8080/`（默认：MCU2）
- `http://localhost:8080/?source=mcu2`
- `http://localhost:8080/?source=mcu3`
- `http://localhost:8080/?source=modelsx_amd`
- `http://localhost:8080/?source=modelsx_intel`

也可以直接指定数据文件：

- `http://localhost:8080/?data=./data/can_frames_decoded_all_values_mcu3.json`

## 功能

- 支持按报文名称、CAN ID、信号名称、枚举表、枚举标签和 VAPI 别名搜索。
- 左右面板独立滚动，便于浏览大型数据集。
- 支持按总线/模块过滤。
- 支持按 CAN ID、名称、信号数量、枚举数量或 VAPI 别名数量排序。
- 在报文详情中直接展开每个信号的已解码枚举值。
- 支持不同数据源切换，例如 MCU2、MCU3、Model S/X AMD、Model S/X Intel。

## 数据说明

- 页面展示的是从 Tesla 固件二进制和 VAPI 信息中提取的研究数据。
- 枚举值主要来自 `Diag_*_map` 类型的枚举表。
- 没有关联枚举表的信号通常只保留信号名称，具体位宽、缩放、单位等信息可能不完整。
- 这些数据不等同于官方 DBC，也不代表 Tesla 官方公开文档。
- 不同车型、硬件版本和固件版本之间，CAN ID、信号名称和枚举值可能存在差异。

## 鸣谢

- Copyright © 2026 Michał Gapiński ([gapinski.eu](https://gapinski.eu))
- Tesla Android ([teslaandroid.com](https://teslaandroid.com/))
- X: [@mikegapinski](https://x.com/mikegapinski)、[@teslaandroid](https://x.com/teslaandroid)

## 许可证

本项目使用 `0BSD` 许可证发布，详情见 `LICENSE`。
