# Template

两份可复用的裸机 RTOS 起始工程索引，以两个自包含的 ZIP 压缩包形式保存。

[English](README.md) | [简体中文](README.zh-CN.md)

## 内容说明

每个平台各一个相互独立的工程模板。它们只是恰好放在同一个仓库中，彼此之间没有构建关系，任何一个都不会构建另一个。

| 平台 | 压缩包 | 内容 |
| --- | --- | --- |
| STM32F407VGT6 | [`STM32/STM32F407VGT6_FreeRTOS.zip`](STM32/STM32F407VGT6_FreeRTOS.zip) | CubeMX 生成的工程，含 HAL、CMSIS，以及 `Middlewares/Third_Party/FreeRTOS` 下的 FreeRTOS。 |
| MSPM0G3507 | [`TI/mspm0g3507_FreeRTOS.zip`](TI/mspm0g3507_FreeRTOS.zip) | CCS/TIClang 的 FreeRTOS 构建，含 `.ccsproject`、`.cproject`、`.project`、`.theia/launch.json` 和 `Debug/` 输出目录。 |

压缩包本身就是交付内容。请不要就地解包重组，也不要把任一 ZIP 当作可丢弃的构建产物——它就是完整的交付物。

## 使用方式

两个压缩包在使用前都解压到新目录，不在 ZIP 内部做任何修改。

**STM32F407VGT6：**

1. 将 `STM32/STM32F407VGT6_FreeRTOS.zip` 解压到工作目录。
2. 打开 `MDK-ARM/` 下的 Keil MDK-ARM 工程；如需重新生成代码，查看 CubeMX 工程（`.ioc`）。
3. 目录中包含 `Core/`、`Drivers/`（CMSIS 与 STM32F4xx HAL）、`Middlewares/Third_Party/FreeRTOS/` 和 `MDK-ARM/`，需一并保留，因为 Keil 工程以相对路径引用它们。

**MSPM0G3507：**

1. 将 `TI/mspm0g3507_FreeRTOS.zip` 解压到工作目录。
2. 在具备 MSPM0 SDK 与 SysConfig 的 TI Code Composer Studio 中导入解压出的工程目录。
3. 压缩包自带 `.ccsproject`、`.cproject` 和 `.project`，可直接导入；其中附带的 `Debug/` 是此前的构建输出，并非导入前提。

**构建状态：未实测。** 撰写本 README 时没有可用的 Keil MDK-ARM 或 Code Composer Studio。上述压缩包内容直接读取自 ZIP 本身，此处没有构建或烧录任何模板。

## 说明

- 两个模板面向不同工具链和不同器件。把它们解压到同一目录不会得到合并后的工程。
- 每个压缩包都内含完整依赖树（HAL/CMSIS/FreeRTOS 或 MSPM0 对应组件），因此 ZIP 相对本仓库的文件数量而言体积较大。
- 模板内容带有各自上游厂商（STMicroelectronics、Texas Instruments、FreeRTOS/Amazon）的版权与许可证声明，这些声明随压缩包一同保留。

## 许可

本仓库中 littleshiraku 的原创贡献（包括原创代码与文档）采用 [MIT 许可证](LICENSE)。在保留版权声明和许可证的前提下，可以使用、修改、再分发及用于商业用途；这些内容不提供任何担保。

第三方代码、文档和其他资料保留各自的版权及许可条款。根目录的 MIT 许可证不重新许可第三方内容，也不授予 littleshiraku 不拥有的权利。

本授权也适用于模板压缩包内的原创贡献。ZIP 内的 STMicroelectronics、Texas Instruments、CMSIS、FreeRTOS 等第三方组件保留原条款，压缩包整体不会因此改为 MIT 许可。
