# st-chatu8-comfydroid

基于 **st-chatu8 v3.1.0** 的集成改造版（SillyTavern / SillyDroid 文生图扩展）。

## 集成内容

- **保留 st-chatu8 全部能力**：多后端（SD / NovelAI / ComfyUI / Grok / Gemini / banana）、ComfyUI 工作流导入与可视化编辑、角色管理（外貌/服装一致性）、LLM 预设与 ToolCall 模式、图片缓存、翻译、tag 锁定、视频生成等。
- **挂载 ComfyDroid 核心模块**（`comfydroid.js`）：
  - Tool Calling 真函数：`comfy_generate_image` / `llm_generate_full_comfy_workflow` / `comfy_submit_workflow` / `comfy_check_progress`
  - 自动构建 ComfyUI 工作流（SDXL Juggernaut + 亚洲脸 LoRA + OpenPose + Hires Fix）
  - 出图质量审查（QualityGate）→ 不合格自动换 seed 重试 / 局部重绘（手/脸/肢体）
  - 漫画分镜（frames/captions）与 2x2 拼页
  - 角色外观锁定、性别铁律（男/女角色不漂移）、多人人数精确、Moody 写实镜头模板
- **配置自动同步**：首次加载自动复用 st-chatu8 已配置的 ComfyUI 地址、尺寸、步数、CFG，无需重复配置。

## 安装

SillyDroid / SillyTavern：`扩展 → 从 URL 安装`，填本仓库 Release 的 zip 直链：

```
https://github.com/aigen-workflow/st-chatu8-comfydroid/releases/latest/download/st-chatu8-comfydroid.zip
```

## 使用

沿用 Comfy 绘图终端角色卡（`comfy_generate_image` 工具）：
用户发中文剧情/分镜要求 → DeepSeek 拆英文 frames + 中文 captions → 本地 ComfyUI 逐格生成 → 拼页返还。

## 许可

随附 LICENSE（Aladdin Free Public License 第 9 版，原作者「从前跟你一样」）。
