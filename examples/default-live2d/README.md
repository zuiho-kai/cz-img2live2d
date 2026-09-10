# 默认 Live2D：小征

这是当前小征的参考模型，随仓库提供。可以先用它看效果、熟悉文件结构和动作驱动，再换成自己的角色。v0.1.1 将左右外侧长发分成独立网格，修正过强惯性和耸肩牵动头发的问题；模型和配套脚本与首页演示录像使用的版本一致。

## 文件

- `model/model.model3.json`：模型入口，引用 MOC3、贴图、表情和待机动作。
- `model/model.moc3`：运行时模型；不是 Cubism 编辑器的 `.cmo3` 工程。
- `model/textures/hair.png`：从原画保留的左右外侧长发；与身体分开绑定，内侧边缘固定以避免露出未绘制区域。
- `runtime/`：小征的待机、状态、口型与发梢驱动。
- `index.html`：直接加载这个默认模型的预览页。
- `provenance.json`：来源、录像标识和文件 SHA-256。

只下载模型时，可用 [默认模型 ZIP](https://github.com/zuiho-kai/cz-img2live2d/releases/download/v0.1.1/changzheng-default-live2d.zip)。ZIP 与本目录内容相同，不含预览依赖。

## 本地看效果

模型已构建好，不需要安装 PuppetLoom、Anime2.5DRig 或重新制作。

网页预览需要在本目录的 `vendor/` 中准备以下运行库。请从你已具备使用权限的运行环境复制；仓库不分发 Cubism Core。

```text
vendor/
  pixi-6.5.10.min.js
  live2dcubismcore.min.js
  cubism4-0.4.0.min.js
```

在本目录启动静态服务：

```powershell
python -m http.server 17875 --bind 127.0.0.1
```

浏览器打开 `http://127.0.0.1:17875/`，默认显示小征并播放待机动作。原生模型也可供兼容 MOC3 的运行环境参考，但只导入模型不会自动带上这里的 JS 表演逻辑；本轮未验证 VTube Studio 导入。

需要接自己的控制器时，在预览页调用 `window.cz.setState('listening')`、`window.cz.setState('thinking')` 或 `window.cz.setState('speaking')`。说话时持续发送 `window.cz.mouth(0到1的数值)`，停止时发送 `window.cz.mouth(0)` 和 `window.cz.setState('idle')`。超过 250 毫秒没有新的口型输入会自动闭嘴。接口说明见预览页源码。

## 参考范围

这是已有小征素材制作的正面表情参考模型，适合检查眨眼、嘴型、身体与头发跟随，以及状态和语音如何接入。本轮只修正已复现的头发问题；没有把所有头发拆成逐束绑定，也没有增加大角度转头。模型质量仍需按具体用途看连续画面判断，不能把加载或口型检查当成整体视觉验收。

角色模型作为本项目的默认参考样例提供；上游代码来源和许可见 [THIRD_PARTY.md](https://github.com/zuiho-kai/cz-img2live2d/blob/main/THIRD_PARTY.md)，运行脚本内保留 Anime2.5DRig 的许可说明。Python wheel 不附带角色模型，请克隆仓库或下载上述 ZIP。
