---
name: mirage-tank-go
description: Generate mirage tank (phantom tank) steganographic PNG images that show different pictures on black vs white backgrounds. Supports grayscale, color, and checkerboard modes.
status: active
version: "v1"
date: "2026-07-18T19:45:00.000Z"
metadata: {"clawdbot":{"emoji":"👻","requires":{"bins":["python3"],"packages":["Pillow","numpy","docopt"]}}}
---

# MirageTankGo - 幻影坦克快速发车工具

## Overview

"幻影坦克" 指点开后不一样的图片：在黑底和白底下显示不同的图片。本 skill 封装
[Aloxaf/MirageTankGo](https://github.com/Aloxaf/MirageTankGo)（上游项目），
让你在 Linux 下也能快速生成这类隐写 PNG。

常用于：把两张图合成一张，黑底显 A、白底显 B（建议用手机 QQ / 深色聊天背景查看效果）。

## Prerequisites

项目已位于 `/root/.openclaw/workspace/MirageTankGo/`。依赖：

```bash
pip3 install Pillow numpy docopt
# tkinter 可选（GUI 模式需要，Windows 自带，Linux 通常需 apt install python3-tk）
```

## Usage

### 命令格式（与上游一致）

```bash
cd /root/.openclaw/workspace/MirageTankGo
python3 MirageTankGo.py -o OUTPUT BLACKIMG WHITEIMG \
    [--scale=WHITESCALE-BLACKSCALE] \
    [--light=WHITELIT-BLACKLIT] \
    [-e | --color=WHITECOL-BLACKCOL]
```

参数含义：
- **BLACKIMG**：在**黑底**下显示的图片
- **WHITEIMG**：在**白底**下显示的图片
- **--scale**：缩放比例，格式 `白底比例-黑底比例`（默认 1-1）
- **--light**：亮度，格式 `白底亮度-黑底亮度`（0~1）
- **-e**：棋盘格模式（仅限灰度车，增强暗部对比）
- **--color**：彩色车模式，色彩保留比例，格式 `白底色彩-黑底色彩`（0~1）
- **--gui**：启动图形界面（需 tkinter）

### 三种模式示例

#### 1. 黑白车（灰度，默认）
```bash
python3 MirageTankGo.py -o out.png black.jpg white.jpg --light=1-0.18
```

#### 2. 彩色车
```bash
python3 MirageTankGo.py -o out.png black.jpg white.jpg --light=1-0.18 --color=0.5-0.7
```

#### 3. 棋盘格（仅灰度）
```bash
python3 MirageTankGo.py -o out.png black.jpg white.jpg --light=1-0.2 -e
```

## Notes

- 输入图最好尺寸一致，工具内部会处理缩放。
- 输出始终为 PNG。
- **黑底图建议足够暗/高对比**，否则在黑底下会几乎消失（常见坑）。
- 查看效果：把生成的 PNG 发到手机 QQ 或垫在纯黑/纯白背景上对比。
- 上游原理参考：知乎「幻影坦克架构指南」系列。

## Agent 使用提示

当用户说"做个幻影坦克图 / 合成两张隐写图 / 黑底白底显示不同图"时：
1. 确认两张输入图路径（黑底图、白底图）。
2. `cd /root/.openclaw/workspace/MirageTankGo` 后运行上述命令。
3. 生成后把 PNG 作为媒体回传，并提示用户在深色/浅色背景下查看差异。
