# ASR1803工具箱

> 随身WiFi & MIFI 开发调试工具

基于 Web Serial API 的浏览器端串口调试工具，专为 ASR1803 芯片随身WiFi/MIFI设备设计。无需安装，Chrome/Edge 打开即用。

## 功能一览

| 功能 | AT 指令 | 说明 |
|------|---------|------|
| IMEI 查询 | `AT+CGSN` | 读取设备 IMEI 号 |
| IMEI 写入 | `AT*MRD_IMEI=W,0,01JAN1970,<imei>` | 写入新 IMEI（含 Luhn 校验） |
| IMEI 删除 | `AT*MRD_IMEI=D` | 清除已写入的 IMEI |
| MAC 查询 | `AT*MRD_WIFIID?` | 读取 WiFi MAC 地址 |
| MAC 写入 | `AT*MRD_WIFIID=W,0,01JAN1970,<mac>` | 写入新 MAC（本地管理位自动设置） |
| MAC 删除 | `AT*MRD_WIFIID=D` | 清除已写入的 MAC |
| SN 查询 | `AT*MRD_SN?` | 读取序列号 |
| SN 写入 | `AT*MRD_SN=W,0,01JAN1970,<sn>` | 写入新 SN |
| SN 删除 | `AT*MRD_SN=D` | 清除已写入的 SN |
| 工厂模式 | `AT*PROD=1` / `AT*PROD=0` | 开启/关闭工厂模式 |
| 设备重启 | `AT+RESET` | 重启设备 |
| SIM 切换 | `AT+SWSIM=0` / `AT+SWSIM=1` | 切换 SIM 卡1 / 卡2 |
| 频段查询 | `AT*BAND?` | 查询当前频段配置 |
| 频段锁定 | `AT* BAND = <params>` | 锁定指定频段（支持 B1/B3/B5/B8/B38/B39/B40/B41） |
| 锁小区 | `AT*CELL=2,3,<band>,<pci>,<arfcn>` | 锁定指定小区 |
| 清除锁小区 | `AT*CELL=0` | 解除小区锁定 |

### 特色功能

- 🎲 **随机生成** — IMEI（Luhn 校验）、MAC（本地管理位）、SN 一键随机
- 🧹 **清空内容** — 快速清空输入框和查询结果
- 📡 **频段可视化** — 勾选复选框锁定频段，查询结果自动回显
- 🔔 **Toast 通知** — 操作结果即时反馈

## 使用方法

1. 用 **Chrome 89+** 或 **Edge 89+** 浏览器打开 `index.html`
2. 通过 USB 连接 ASR1803 设备
3. 选择波特率（默认 115200），点击「连接」
4. 在浏览器弹出的串口选择器中选择对应端口
5. 连接成功后即可使用各项功能

> ⚠️ Web Serial API 仅在 HTTPS 或 localhost 下可用，直接打开本地 HTML 文件也支持。

## 支持的频段

| 频段 | 类型 | AT 参数 |
|------|------|---------|
| B1 | FDD-LTE | `,0,1,0,2,2,0` |
| B3 | FDD-LTE | `,0,4,0,2,2,0` |
| B5 | FDD-LTE | `,0,16,0,2,2,0` |
| B8 | FDD-LTE | `,0,128,0,2,2,0` |
| B38 | TDD-LTE | `,32,0,0,2,2,0` |
| B39 | TDD-LTE | `,64,0,0,2,2,0` |
| B40 | TDD-LTE | `,128,0,0,2,2,0` |
| B41 | TDD-LTE | `,256,0,0,2,2,0` |

## 技术栈

- **前端**：纯 HTML + CSS + JavaScript（零依赖）
- **串口通信**：Web Serial API
- **UI 设计**：紫蓝色（`#6C5CE7` + `#0984E3`）深色卡片式主题
- **动态效果**：Canvas 粒子背景、卡片悬停动画、结果淡入

## 浏览器兼容性

| 浏览器 | 最低版本 |
|--------|----------|
| Google Chrome | 89+ |
| Microsoft Edge | 89+ |
| Opera | 75+ |

> Firefox 和 Safari 目前不支持 Web Serial API。

## 项目起源

本项目从「西瓜味ASR终版.exe」（.NET WinForms 应用）逆向提取 AT 指令和功能逻辑，使用 Web 技术重写为现代浏览器应用，无需安装 .NET 运行时，跨平台即开即用。

## 版权信息

**B站@氢境** | [https://space.bilibili.com/352977016](https://space.bilibili.com/352977016)

## License

MIT
