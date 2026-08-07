# AI8051U 创新项目

基于 STC AI8051U 单片机的综合外设驱动库项目，使用 AI8051U 专属库函数进行开发。

## 芯片简介

AI8051U 是 STC 推出的增强型 8051 内核单片机，集成 **MDU32**（32位硬件乘除法单元）和 **TFPU**（三角函数浮点运算单元），支持硬件数学加速，主频高达 42MHz，适用于工业控制、电机驱动、传感器采集等场景。

## 库函数功能

本项目整合了 AI8051U 完整的外设驱动库，涵盖以下模块：

| 编号 | 模块     | 功能说明                                   | 源文件                                      |
|------|----------|-------------------------------------------|---------------------------------------------|
| 1    | IO       | 并行IO控制（含IO独立中断）                   | [set_io.c](set_io.c) [set_io.h](set_io.h)         |
| 2    | 定时器   | T0/T1/T2/T3/T4/T11 定时器及外部中断        | [set_timer.c](set_timer.c) [set_timer.h](set_timer.h) |
| 3    | 串口     | UART通信（含串口DMA）                        | [set_uart.c](set_uart.c) [set_uart.h](set_uart.h)   |
| 4    | ADC      | 12位ADC，支持连续/单次自动转换               | [set_adc.c](set_adc.c) [set_adc.h](set_adc.h)       |
| 5    | I2C      | 主机/从机模式，自由组合指令串操作             | [set_i2c.c](set_i2c.c) [set_i2c.h](set_i2c.h)       |
| 6    | SPI      | 高速同步串行通信（含SPI-DMA）                | [set_spi.c](set_spi.c) [set_spi.h](set_spi.h)       |
| 7    | PWM      | 基础PWM输出控制                              | [set_pwm.c](set_pwm.c) [set_pwm.h](set_pwm.h)       |
| 8    | EEPROM   | 片内EEPROM读写（含均衡磨损算法）             | [set_eeprom.c](set_eeprom.c) [set_eeprom.h](set_eeprom.h) |
| 9    | 协程     | 协程式多任务调度（资源占用极少）             | [set_task.c](set_task.c) [set_task.h](set_task.h)   |
| —    | IO中断   | 独立的IO口电平变化中断                       | [io_int.c](io_int.c) [io_int.h](io_int.h)            |

## 库依赖（LIB文件）

| 文件 | 说明 |
|------|------|
| [AI8051U_32_MDU32.LIB](AI8051U_32_MDU32.LIB) | 32位硬件乘除法单元库 |
| [AI8051U_32_TFPU.LIB](AI8051U_32_TFPU.LIB) | 三角函数浮点运算单元库 |
| [stc_usb_cdc_32g.LIB](stc_usb_cdc_32g.LIB) | USB-CDC 虚拟串口通讯库 |

## 开发环境

- **IDE**: Keil C51
- **芯片型号**: AI8051U-32bit（251指令集）
- **编程语言**: C

### 注意事项

使用前需安装 **Keil 中断向量号拓展插件**：
- 复制插件 EXE 到 Keil 安装目录 `C51\BIN\` 下运行
- 勾选 `Use Expanded 251C Interrupt Vector` 选项

## 应用示例

基于库函数的独立例程：

| 编号 | 示例              | 说明                    |
|------|-------------------|-------------------------|
| 1    | IO 测试           | 并行IO输入/输出与独立中断 |
| 2    | 定时器测试        | 定时器中断与外部中断     |
| 3    | 串口测试          | UART收发（含DMA）       |
| 4    | ADC 测试          | 模数转换采集            |
| 5    | I2C 测试          | I2C设备通讯             |
| 6    | SPI 测试          | SPI设备通讯（含DMA）    |
| 7    | PWM 测试          | PWM波形输出             |
| 8    | EEPROM 测试       | 片上EEPROM读写          |
| 9    | 协程任务调度测试   | 多任务协程调度          |
| 10   | 协程应用案例       | 交通灯/蜂鸣器/按键消抖  |
| 11   | MPU6050 陀螺仪    | I2C读取MPU6050姿态数据   |
| 12   | AD9833 DDS模块    | SPI控制DDS波形发生器    |

## 项目结构

```
.
├── main.c                    # 主程序
├── ai8051u_templete.uvproj   # Keil 项目文件
├── AI8051U_32_MDU32.LIB      # MDU 运算库
├── AI8051U_32_TFPU.LIB       # TFPU 运算库
├── stc_usb_cdc_32g.LIB       # USB-CDC 通讯库
├── set_io.c / .h             # IO 驱动
├── set_timer.c / .h          # 定时器驱动
├── set_uart.c / .h           # 串口驱动
├── set_adc.c / .h            # ADC 驱动
├── set_i2c.c / .h            # I2C 驱动
├── set_spi.c / .h            # SPI 驱动
├── set_pwm.c / .h            # PWM 驱动
├── set_eeprom.c / .h         # EEPROM 驱动
├── set_task.c / .h           # 协程调度
├── set_int.c / .h            # 外部中断
├── io_int.c / .h             # IO 中断
└── README.md
```

## 许可证

STC AI8051U 专属库函数 © 宏晶科技（STC Micro）。

本项目仅用于学习和开发参考。