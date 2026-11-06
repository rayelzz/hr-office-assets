# HR 办公室静态资源

用于飞书页面副本试验的只读办公室渲染包。使用 GitHub Pages 提供静态 HTTPS 文件，不包含业务后端。

## 内容

- `office-renderer.v20261106.1.js`：React、Pixi、办公室场景、人物原帧动画与图资源；独立 IIFE，无运行时 npm/CDN 依赖。
- `manifest.json`：版本、来源提交及 SHA256。
- `LICENSE.txt`、`THIRD_PARTY_NOTICES.txt`：软件许可和依赖声明。

## 接入

将渲染包作为普通脚本载入，调用 `window.BossHROffice.mountOffice(host, props)`。返回实例支持 `update(partialProps)` 与 `destroy()`，使用 Shadow DOM 隔离宿主样式。

`props` 由宿主传入快照、明暗主题和查看分析回调。真实账号、JD、寻访记录及凭据不放在本仓库；没有接收这些数据的接口。前端构件中仅保留展示模型所需字段标识。

## 原作来源

[workbzw/pixoffice](https://github.com/workbzw/pixoffice)，固定提交 `94ce6060ff640e9198f95518699c5f2ce3fcdb0b`。复用原 FrameSprite、帧采样、CharacterPackResources、DeskEntity 及原房间、桌椅、电脑和六套人物图片，创建八个独立工位实例。图片经过WebP 压缩与原帧图集合并，没有使用整张设计效果图冒充交互场景。

原代码按 MIT 许可保留声明。上游明确说明其软件依赖许可清单不确立图片素材的授权，本仓库同样不为第三方图片赋予额外许可；来源说明见 [上游许可说明](https://github.com/workbzw/pixoffice/blob/main/licenses/README.md)。

## 部署

GitHub Pages 从 `main` 根目录发布，`.nojekyll` 保留版本化静态文件。加载方应固定带版本的文件名，更新时使用新文件名并核对 `manifest.json`。
