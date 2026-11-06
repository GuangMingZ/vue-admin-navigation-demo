# Vue Element Admin 导航 Demo 归档

本目录保存 `oneid-vision-agent` 在本地 `vue-element-admin` 上运行导航演示后生成的示例产物。

它不是可执行的 Agent 源码，也不包含被测项目源码。目录中的内容用于复盘一次已完成的浏览器会话，并为技术分享、走查或问题定位提供截图与结构化证据。

## 本次演示覆盖

- 自动登录本地 `vue-element-admin`
- 巡航 13 个包含表格的路由并保存页面截图
- 在行内编辑表中，以 SoM 编号辅助视觉模型定位 ID 为 6 的 `Edit`
- 写入并读回 `VLM edited title`，验证目标行进入编辑态
- 经侧栏进入 Drag Dialog，按 AST 识别出的入口打开并校验 `Shipping address` 弹窗

本次归档共包含 15 个页面状态。运行时间与每条状态的来源、截图路径和备注见 `capture-manifest.json`。

## 文件说明

| 路径 | 内容 |
| --- | --- |
| `index.html` | 可直接在浏览器中打开的截图画廊 |
| `summary-report.md` | 归档状态的简要 Markdown 报告 |
| `capture-manifest.json` | 机器可读的场景、路由、截图、时间与验收记录 |
| `snapshots/` | 路由巡航、行内编辑和弹窗校验的完整截图 |
| `vlm/` | SoM 编号截图与 ID 为 6 的行内编辑结果 |
| `table-pages/` | 表格路由截图的备用整理目录 |
| `drag-dialog-opened.png` | Drag Dialog 打开并完成标题校验后的便捷副本 |

## 查看方式

直接打开 `index.html` 即可查看页面状态与截图。若浏览器对本地文件加载有限制，可以在本目录启动静态文件服务。

```bash
python3 -m http.server 8000
```

然后访问 <http://127.0.0.1:8000>。

## 如何解读证据

`capture-manifest.json` 中每条记录对应一次已归档的页面状态。

- `sceneId` 用于稳定标识场景
- `pageUrl` 记录演示时的本地访问地址
- `sourceLocation` 记录路由或源码位置
- `variantLabel` 区分常规巡航与特定交互状态
- `evidenceStatus` 表示归档状态
- `captureNote` 记录本次截图的验收说明

行内编辑场景与 Drag Dialog 场景是两条独立的交互证据。前者证明同文案操作经过视觉消歧后落在目标行，后者证明 AST 给出的入口文本能够在运行态定位，并以弹窗标题完成验收。

## 数据与使用边界

被测对象为本地运行的开源示例项目，演示使用固定示例账号和页面自带的演示数据。本目录不应被当作生产环境审计结果，也不能替代对真实业务权限、数据与风险动作的验证。
