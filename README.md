# MirageTankGo - 幻影坦克技能

生成幻影坦克（phantom tank）隐写 PNG 图片，黑底和白底显示不同的图片。

## 用法

```bash
cd /root/.openclaw/workspace/MirageTankGo
python3 MirageTankGo.py -o output.png black.jpg white.jpg
```

## 参数

- `BLACKIMG`：在黑底下显示的图片
- `WHITEIMG`：在白底下显示的图片
- `--scale`：缩放比例（格式 `白底比例-黑底比例`）
- `--light`：亮度（格式 `白底亮度-黑底亮度`）
- `-e`：棋盘格模式（灰度）
- `--color`：彩色模式（格式 `白底色彩-黑底色彩`）
- `--gui`：启动图形界面

## 依赖

- Pillow
- numpy
- docopt
