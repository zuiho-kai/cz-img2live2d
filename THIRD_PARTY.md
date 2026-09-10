# Sources

- PuppetLoom：`https://github.com/CheshireMew/PuppetLoom`，锁定 `f26c83dd31a48c644eb962971b9e21b9fa06f3f4`。上游 package.json 标注 `AGPL-3.0-or-later`。本包通过独立 checkout 的 CLI 和 Web SDK 适配；生成预览复制其 LICENSE。
- Anime2.5DRig：`https://github.com/852wa/Anime2.5DRig`，锁定 `7450341934a8ff77bf05b90d9f708786e3eb3996`。MIT，Copyright (c) 2026 hakoniwa。绑定与补件使用原始 rigger/genericparts；预览保持原始 app 的渲染算法，仅注入 agent 桥。生成产物保存来源许可。
- image2live2d：`https://github.com/Wzhang3912/image2live2d`，锁定 `b3fea7536f2d680897dbf5cce5a13046da75803c`。Apache-2.0。仅作为长征已使用的低层 MOC3 writer，通过显式配置路径加载，不在包内复制该项目源码。
- 长征：来源 [zuiho-kai/changzheng](https://github.com/zuiho-kai/changzheng)，本项目从其提交 `6bed07fae118a67a7e2094f5b3682d61471f2326` 的 `packages/cz-img2live2d/` 提取为独立仓库。原始来源包括 `probes/build_expression_rig.py` 与 2026-09-10 模拟器修复后 `avatar-performance.js`、`secondary-motion.js`。原始来源及当前包内源码哈希见 `changzheng-provenance.json`。v0.1.1 在显式路径适配之外，增加了左右外侧长发的独立网格，修正物理角度换算与袖子变形范围；原画像素保持，仍保留小征原模板的坐标限制。
- `secondary-motion.js` 内的 spring 来自 Anime2.5DRig；随源码保留 `ANIME25D-LICENSE.txt`。

Python 安装包不附带用户角色原画、测试 PSD、上游示例素材或 Cubism Core。仓库的 `examples/default-live2d/` 另行提供用户指定的小征默认参考模型、贴图和配套运行脚本，来源及文件哈希见该目录的 `provenance.json`；首页 GIF 和 Release 视频取自相同版本的实际排练。测试使用现有本地素材；这些素材的实际使用范围与软件源码分开记录。导出包的上游许可、运行时依赖和素材来源应随产物保留。
