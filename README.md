# 御风青鸾 · 立体光栅卡

**在线地址 → https://mbsskdy.github.io/qingluan-card/**

一张会随视角变形、会闪的立体光栅卡。主体是从卡面里飞出来的立体，环境里的水一直在流。

![动态预览](preview.gif)

---

## 怎么看

打开上面的链接就行，手机和电脑都可以，不用装任何东西。

- **拖动**：左右拖 = 卡片转动，能看出人物浮在卡面之上
- **滑块**：调景深、光泽、画面比例
- **点一下**：翻到背面
- **保存按钮**：把当前画面存成图片

## 这一版做了什么

卡面 `1536×1024` 横版，五层：

| 层 | 位置 | 作用 |
| --- | --- | --- |
| 底 | `-0.50` | 卡纸底 |
| 环境 | `-0.12` | 循环流动的水（107 帧无缝循环视频） |
| 主体 | `0` | 人物——**真实厚度**，不是贴图 |
| 特效 | `+0.16` | 光珠、星芒 |
| 文字 | `+0.40` | 卡名与工艺字 |

立体感来自真几何：主体用厚度图（`assets/subject-height.png`）驱动 `384×256` 网格顶点，沿卡面法线抬升 `0.45`，侧壁法线随视角变化自己算亮暗。**没有画描边** —— 描边在正面看会变成一圈黑边，反而更假。

## 文件

```
index.html           页面
style.css            样式
app.bundle.js        查看器（three.js 内联，单文件）
card-config.json     卡面配置：文案、配色、各层深度
assets/
  subject.png        主体（带透明通道）
  subject-height.png 主体厚度图
  background.png     背景
  lineart.png        线稿
  water.png          水面
  effects.png        特效
  text.png           文字
  card.glb           卡片几何
  env.mp4            环境循环动画（107 帧 / 24fps / 无缝）
preview.gif          动态预览
```

想改文案、配色或各层深度，改 `card-config.json` 即可，不用重新打包。

## 版权

画面为本作品原创，保留所有权利。页面代码基于
[guangshanka-skill](https://github.com/mbsskdy/guangshanka-skill) 生成。