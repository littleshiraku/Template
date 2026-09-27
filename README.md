# Template

A small index of reusable bare-metal RTOS starting points, stored as two self-contained ZIP archives.

[English](README.md) | [简体中文](README.zh-CN.md)

## What Is Here

Two independent project templates, one per platform. They are unrelated projects that happen to live in the same repository; neither one builds the other.

| Platform | Archive | Contents |
| --- | --- | --- |
| STM32F407VGT6 | [`STM32/STM32F407VGT6_FreeRTOS.zip`](STM32/STM32F407VGT6_FreeRTOS.zip) | CubeMX-generated project with HAL, CMSIS, and FreeRTOS in `Middlewares/Third_Party/FreeRTOS`. |
| MSPM0G3507 | [`TI/mspm0g3507_FreeRTOS.zip`](TI/mspm0g3507_FreeRTOS.zip) | CCS/TIClang FreeRTOS build with `.ccsproject`, `.cproject`, `.project`, `.theia/launch.json` and a `Debug/` output tree. |

The archives are the deliverable. Do not unpack and repack them in place, and do not treat either ZIP as disposable build output - it is the entire artifact.

## Using a Template

Both archives are extracted into a fresh directory before use; nothing is edited inside the ZIP.

**STM32F407VGT6:**

1. Extract `STM32/STM32F407VGT6_FreeRTOS.zip` into a working directory.
2. Open the Keil MDK-ARM project under `MDK-ARM/` and inspect the CubeMX project (`.ioc`) if you need to regenerate code.
3. The tree keeps `Core/`, `Drivers/` (CMSIS and STM32F4xx HAL), `Middlewares/Third_Party/FreeRTOS/` and `MDK-ARM/`; keep them together, since the Keil project references them by relative path.

**MSPM0G3507:**

1. Extract `TI/mspm0g3507_FreeRTOS.zip` into a working directory.
2. Import the extracted project folder into TI Code Composer Studio with the MSPM0 SDK and SysConfig available.
3. The archive carries its own `.ccsproject`, `.cproject` and `.project`, so it is importable as-is; the bundled `Debug/` directory is a prior build output, not a requirement.

**Build status: not verified.** Neither Keil MDK-ARM nor Code Composer Studio was available when this README was written. The archive contents above were read from the ZIPs themselves; no template was built or flashed here.

## Notes

- The two templates target different toolchains and different devices. Extracting both into one directory will not produce a combined project.
- Each archive contains its full dependency tree (HAL/CMSIS/FreeRTOS or the MSPM0 equivalents), so the ZIPs are large relative to the number of files in this repository.
- The template contents carry the copyright and license notices of their originating vendors (STMicroelectronics, Texas Instruments, FreeRTOS/Amazon). Those notices travel inside the archives.

## License

Original contributions by littleshiraku in this repository, including original code and documentation, are licensed under the [MIT License](LICENSE). You may use, modify and redistribute these contributions, including commercially, provided that you retain the copyright and license notice. They are provided without warranty.

Third-party code, documents and other materials retain their respective copyrights and licenses. The root MIT license does not relicense third-party material or grant rights that littleshiraku does not hold.

This also applies to original contributions within the template archives. Vendor code inside the ZIPs, including STMicroelectronics, Texas Instruments, CMSIS and FreeRTOS components, retains its original terms; the archives are not wholly relicensed under MIT.
