# MiniMax H3 低显存工作流 / Low VRAM Workflows

MiniMax H3 视频生成工作流，适配 **4GB / 6GB / 8GB 显存**显卡。

Low VRAM workflows for MiniMax H3 video generation, targeting **4GB / 6GB / 8GB** GPUs.

## 工作流列表 / Workflow List

5 种模式 × 3 档显存 = 15 个基础 + 3 个带 LoRA 扩展 = **18 个**

| # | 模式 / Mode | 4G | 6G | 8G | 说明 / Notes |
|---|---|---|---|---|---|
| 1 | 文生视频 T2V | ✅ | ✅ | ✅ | 纯文本生成视频 / text-to-video |
| 2 | 图生视频 I2V | ✅ | ✅ | ✅ | 图片参考生成 / image-to-video |
| 3 | 首尾帧 FL2V | ✅ | ✅ | ✅ | 首帧+尾帧生成 / first-last-frame |
| 4 | 多图参考 REF | ✅ | ✅ | ✅ | 多图参考 / multi-image reference |
| 5 | 多图+音频 REFA | ✅ | ✅ | ✅ | 多图+音频参考 / multi-image + audio |

加 LoRA 扩展（4G/6G/8G T2V 各一个）在 `workflows/` 中以 `加LoRA` 结尾。

## 使用 / Usage

1. 安装 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) + MiniMax H3 自定义节点
2. 下载模型文件（见下方）
3. 将 JSON 导入 ComfyUI

## 所需模型 / Required Models

| 模型 / Model | 用途 / Purpose |
|---|---|
| `minimax_h3_fl2va_pruned_int8_convrot.safetensors` | 主模型 / main model |
| `qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors` | 文本编码器 / text encoder |
| `minimax_h3_video_vae_int8_convrot.safetensors` | 视频 VAE |

## LoRA 说明 / LoRA Note

`加LoRA` 工作流中的 LoRA 节点**默认为空**（不加载任何 LoRA）。在 `LoraLoaderModelOnly` 节点选择你自己的 LoRA，`strength_model = 0` 即关闭。

The LoRA node in `加LoRA` workflows is **empty by default**. Pick your own LoRA in `LoraLoaderModelOnly`; `strength_model = 0` disables it.

## 致谢 / Credits

原始工作流来自熊猫怪兽分享的 H3_4G_6G_8G 工作流包，按模式拆分为独立文件。

Original workflows from 熊猫怪兽分享's H3_4G_6G_8G pack, split into standalone files by mode.

## License

MIT
