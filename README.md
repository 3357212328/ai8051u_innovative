# AI8051U 创新项目

基于 STC AI8051U 单片机的综合外设驱动库项目，使用 **AI8051U 专属库函数**（位于 `D:\embeded electronic\stc\AI8051U专用库函数\`）进行开发。

## 芯片简介

AI8051U 是 STC 推出的增强型 8051 内核单片机，集成 **MDU32**（32位硬件乘除法单元）和 **TFPU**（三角函数浮点运算单元），支持硬件数学加速，主频高达 42MHz，适用于工业控制、电机驱动、传感器采集等场景。

## 开发环境

- **IDE**: Keil C251
- **芯片型号**: AI8051U-32bit（251指令集）
- **编程语言**: C

---

## 一、AI8051U 专属库函数

> 库函数源目录：`D:\embeded electronic\stc\AI8051U专用库函数\`

本项目整合了 AI8051U 完整的外设驱动库，涵盖以下模块：

| 编号 | 模块     | 功能说明                                   | 源文件                                      |
|------|----------|-------------------------------------------|---------------------------------------------|
| 1    | IO       | 并行IO控制（含IO独立中断）                 | [set_io.c](set_io.c) [set_io.h](set_io.h)         |
| 2    | 定时器   | T0/T1/T2/T3/T4/T11 定时器及外部中断        | [set_timer.c](set_timer.c) [set_timer.h](set_timer.h) |
| 3    | 串口     | UART通信（含串口DMA）                      | [set_uart.c](set_uart.c) [set_uart.h](set_uart.h)   |
| 4    | ADC      | 12位ADC，支持连续/单次自动转换              | [set_adc.c](set_adc.c) [set_adc.h](set_adc.h)       |
| 5    | I2C      | 主机/从机模式，自由组合指令串操作           | [set_i2c.c](set_i2c.c) [set_i2c.h](set_i2c.h)       |
| 6    | SPI      | 高速同步串行通信（含SPI-DMA）              | [set_spi.c](set_spi.c) [set_spi.h](set_spi.h)       |
| 7    | PWM      | 基础PWM输出控制                            | [set_pwm.c](set_pwm.c) [set_pwm.h](set_pwm.h)       |
| 8    | EEPROM   | 片内EEPROM读写（含均衡磨损算法）           | [set_eeprom.c](set_eeprom.c) [set_eeprom.h](set_eeprom.h) |
| 9    | 协程     | 协程式多任务调度（资源占用极少）           | [set_task.c](set_task.c) [set_task.h](set_task.h)   |
| —    | IO中断   | 独立的IO口电平变化中断                     | [io_int.c](io_int.c) [io_int.h](io_int.h)            |

### 库依赖（LIB 文件）

| 文件 | 说明 |
|------|------|
| [AI8051U_32_MDU32.LIB](AI8051U_32_MDU32.LIB) | 32位硬件乘除法单元库 |
| [AI8051U_32_TFPU.LIB](AI8051U_32_TFPU.LIB) | 三角函数浮点运算单元库 |
| [stc_usb_cdc_32g.LIB](stc_usb_cdc_32g.LIB) | USB-CDC 虚拟串口通讯库 |

### 库函数独立例程

> 位于 `D:\embeded electronic\stc\AI8051U专用库函数\独立例程\`

| 编号 | 示例              | 说明                    |
|------|-------------------|-------------------------|
| 1    | IO 测试           | 并行IO输入/输出与独立中断 |
| 2    | 定时器测试       | 定时器中断与外部中断     |
| 3    | 串口测试         | UART收发（含DMA）        |
| 4    | ADC 测试         | 模数转换采集             |
| 5    | I2C 测试         | I2C设备通讯              |
| 6    | SPI 测试         | SPI设备通讯（含DMA）     |
| 7    | PWM 测试         | PWM波形输出              |
| 8    | EEPROM 测试      | 片上EEPROM读写           |
| 9    | 协程任务调度测试 | 多任务协程调度           |
| 10   | 协程应用案例集锦 | 交通灯 / 蜂鸣器 / 按键消抖 |
| 11   | MPU6050 陀螺仪   | I2C读取MPU6050姿态数据    |
| 12   | AD9833 DDS 模块  | SPI控制DDS波形发生器     |

---

## 二、AI8051U 实验箱示例代码（V1.2）

> 源目录：`D:\embeded electronic\stc\AI8051U-DEMO-CODE-V1.2\`

STC 官方为 AI8051U 实验箱提供的完整示例代码，包含 32-bit 和 8-bit 两种模式，覆盖所有片上外设与常用扩展模块。

### 基础外设（01-22）

| 编号 | 示例 | 说明 |
|------|------|------|
| 01 | 用P0口做跑马灯 | GPIO基础输出 |
| 02 | Timer0/1/2/3/4测试程序 | 全部5路定时器 |
| 03.1 | IO口控制74HC595驱动8个数码管 | 串并转换基础 |
| 03.2 | 硬件SPI控制74HC595驱动数码管 | SPI外设驱动数码管 |
| 04 | 利用T0/T1引脚做外部计数器 | 定时器计数模式 |
| 05 | 定时器1测量INT1引脚低电平脉冲宽度 | 脉冲宽度测量 |
| 06 | 主时钟停振低功耗模式-唤醒定时器唤醒 | 低功耗模式 |
| 07 | 主时钟停振低功耗模式-外部中断唤醒 | 外部唤醒 |
| 08 | 看门狗复位测试程序 | 看门狗功能验证 |
| 09 | 软件设置CPU内部时钟源 | HIRC/PLL/IRC32K |
| 10 | 串口1中断模式收发测试 | UART1基础通讯 |
| 11 | 串口2中断模式收发测试 | UART2基础通讯 |
| 12 | 串口3中断模式收发测试（需飞线） | UART3通讯 |
| 13 | 串口4中断模式收发测试（需飞线） | UART4通讯 |
| 14.1 | 串口1/串口2同时与电脑收发 | 双串口并发 |
| 14.2 | 串口1与串口2通信测试 | 串口间互发 |
| 14.3 | 外中断INT0/INT1/INT2/INT3/INT4测试 | 5路外部中断计数 |
| 15 | IO行列扫描按键 | 矩阵按键+数码管 |
| 16 | ADC检测16个按键 | ADC按键检测 |
| 17 | ADC采集NTC热敏电阻测温 | 温度采集 |
| 18 | ADC测量内部1.19V信号源计算VCC | 内基准电压测量 |
| 19 | 串口命令读写EEPROM | EEPROM读写 |
| 20 | LVD低压检测中断保存EEPROM | 低压检测 |
| 21 | 比较器正极P4.6，负极内部1.19V | 比较器应用 |
| 22 | 比较器检测外部稳压管掉电保存EEPROM | 掉电保护 |

### 显示与音频（36-38, 75-78, 87）

| 编号 | 示例 | 说明 |
|------|------|------|
| 36.1 | LCD1602 IO模拟M6800并行接口 | 字符LCD |
| 36.2 | LCD1602 硬件M6800并行接口驱动 | 硬件并口加速 |
| 36.3 | LCD1602 硬件M6800+DMA刷新 | DMA自动刷新 |
| 36.4 | LCD128x64-ST7920-IO模拟M6800 | 图形12864 LCD |
| 37.1 | 2.4寸ILI9341 TFT-IO模拟I8080 | 彩色TFT触摸屏 |
| 37.2 | 2.4寸ILI9341 TFT-硬件I8080 | 硬件并口TFT |
| 37.3 | 2.4寸ILI9325 TFT-IO模拟I8080 | 另一种TFT驱动IC |
| 37.4 | 2.4寸ILI9325 TFT-硬件I8080 | 硬件并口TFT |
| 38 | 3.5寸ILI9486驱动TFT显示屏 | 大尺寸TFT |
| 75 | LCD128x64 ST7920 DMA-M6800刷新 | DMA刷新图形LCD |
| 76 | 1.3寸ST7789 TFT240x240 SPI-DMA刷屏 | 小尺寸SPI彩屏 |
| 77 | DMA SPI刷新OLED12864-SSD1306 | 0.96寸OLED |
| 78 | DMA SPI刷新LCD12864-ST7565R | 1.44寸LCD |
| 87 | U8G2 DMA OLED | U8g2图形库移植 |

### PWM与电机控制（23-26, 68, 83）

| 编号 | 示例 | 说明 |
|------|------|------|
| 23 | PCA型PWM输出呼吸灯 | 基础PWM |
| 24 | P0口呼吸灯 | 高级PWM1~4 |
| 25 | 高级PWM5~8呼吸灯 | 高级PWM5~8 |
| 26 | PWM驱动无源蜂鸣器 | 蜂鸣器音调 |
| 68 | 高速HS-PWM1~4呼吸灯 | 高速PWM |
| 83 | 高级PWM硬件移相 | 移相控制 |

### USB 协议栈（42-52, 74, 84）

| 编号 | 示例 | 说明 |
|------|------|------|
| 42 | USB-HID协议范例 | HID基础 |
| 43 | USB-CDC协议范例 | 虚拟串口 |
| 44 | USB-HID键盘范例 | 模拟键盘 |
| 45 | USB-HID鼠标范例 | 模拟鼠标 |
| 46 | WINUSB协议范例 | WinUSB通讯 |
| 47 | MSD协议范例-U盘演示 | 模拟U盘 |
| 48 | USB-HID发送指令读取ADC | HID指令交互 |
| 49 | USB HID协议打印数据信息 | HID调试打印 |
| 50 | ISP调试接口/CDC虚拟设备 | 虚拟键盘/虚拟OLED12864等 |
| 51 | USB-CDC转双串口 | 双串口桥接 |
| 52 | USB鼠标-键盘复合设备 | 复合设备 |
| 74 | USB声卡-TLV320AIC23B | 音频声卡 |
| 84 | USB录放音声卡-TLV320AIC23B | 录放音声卡 |

### DMA 应用（60-66, 71-72, 79-80）

| 编号 | 示例 | 说明 |
|------|------|------|
| 60 | DMA-ADC采样数据自动存储 | DMA+ADC |
| 61 | DMA-M2M存储器间读写 | 存储器间读写 |
| 62 | DMA-SPI数据自动收发 | SPI读写 |
| 63 | DMA-QSPI-P2P访问QSPI Flash | QSPI访问 |
| 64 | DMA-UART串口数据自动收发 | UART收发 |
| 65 | DMA-LCD12864/TFT显示 | 液晶屏DMA刷新 |
| 66 | DMA-I2C读写AT24C02 | I2C读取 |
| 71.1 | 串口发送图片->SPI Flash->TFT DMA交替显示(ILI9341) | 图片显示 |
| 71.2 | 同上(ILI9325) | 图片显示 |
| 72.1 | UART-SPI-TFT DMA P2P显示图片 | 外设到外设 |
| 72.2 | QSPI-TFT DMA P2P图片 | QSPI模式 |
| 72.3 | QSPI-TFT DMA P2P视频动画(ILI9325) | 视频级刷新 |
| 72.4 | QSPI-TFT DMA P2P视频动画(ILI9341) | 视频级刷新 |
| 79 | TFT彩屏8位数据口搭R-2R电阻做DAC通过DMA输出波形 | 自制DAC |
| 80 | SPI-DMA驱动WS2812彩灯 | 数字彩灯 |

### 其他外设与应用（27-35， 39-41， 56-59， 69-70， 73， 81-82， 85-86）

| 编号 | 示例 | 说明 |
|------|------|------|
| 27 | 定时器周期性调度任务 | 简易任务调度 |
| 28 | I2C主机模式读AT24C02 | EEPROM读写 |
| 29 | 红外接收信号(NEC码) | 红外遥控 |
| 30 | 红外发射(NEC码)-PWM4产生38KHz载波 | 红外发送 |
| 31 | 按键命令红外发送 | 红外收发一体 |
| 32 | 硬件SPI访问FLASH | SPI Flash |
| 33 | IO模拟SPI访问FLASH | 软SPI Flash |
| 34 | 硬件QSPI访问SPI FLASH | QSPI |
| 35 | 板载外部扩展32K xdata测试 | XRAM |
| 39 | DS18B20测温 | 一线制传感器 |
| 40 | MDU32乘除法单元 | MDU32测试 |
| 41 | 内部RTC时钟-外部32768晶振 | RTC |
| 56 | LIN总线从机收发测试-USART1 | LIN从机 |
| 57 | LIN总线主机收发测试-USART1 | LIN主机 |
| 58 | LIN总线从机收发测试-USART2 | LIN从机 |
| 59 | LIN总线主机收发测试-USART2 | LIN主机 |
| 69 | USART1设为SPI访问Flash | UART转SPI |
| 70 | USART1与USART2作为SPI相互通信 | UART转SPI互发 |
| 73 | 频谱分析256点FFT-CDC | FFT绘图显示 |
| 81 | I2S播放FLASH中的立体声ADPCM音乐 | 音频播放 |
| 82 | I2S数字录放音 | 录音回放 |
| 85 | 示波器-CDC虚拟显示 | 虚拟示波器 |
| 86 | 普通IO口中断-休眠唤醒 | IO中断唤醒 |

### 不停电下载（A01~A04）

| 编号 | 示例 | 说明 |
|------|------|------|
| A01 | P3.2按键触发软复位到系统区 | 按键触发 |
| A02 | USB-CDC命令触发软复位 | CDC命令不停电下载 |
| A03 | USB-HID命令触发软复位 | HID命令不停电下载 |
| A04 | UART命令触发软复位 | UART命令不停电下载 |

---

## 项目结构

```
.
├── main.c                    # 主程序
├── ai8051u_templete.uvproj   # Keil 项目文件
├── AI8051U_32_MDU32.LIB      # MDU 运算库
├── AI8051U_32_TFPU.LIB       # TFPU 运算库
├── stc_usb_cdc_32g.LIB       # USB-CDC 通讯库
├── set_adc.c / .h             # ADC 驱动
├── set_eeprom.c / .h          # EEPROM 驱动
├── set_i2c.c / .h             # I2C 驱动
├── set_int.c / .h             # 外部中断
├── set_io.c / .h             # IO 驱动
├── set_pwm.c / .h             # PWM 驱动
├── set_spi.c / .h             # SPI 驱动
├── set_timer.c / .h           # 定时器驱动
├── set_uart.c / .h            # 串口驱动
├── set_task.c / .h            # 协程调度
├── io_int.c / .h              # IO 独立中断
├── .gitignore
└── README.md
```

## 许可证

STC AI8051U 专属库函数 © 宏晶科技（STC Micro）。

AI8051U 实验箱示例代码 V1.2 © 宏晶科技（STC Micro）。

本项目仅用于学习和开发参考。