---
name: grok-video
description: Write Grok Imagine video prompts for text-to-video and image-to-video in the Grok app. Trigger on Grok视频, Imagine, 图生视频, 参考图生视频, 生成视频提示词, or when the user uploads a still to animate.
metadata:
  audience: grok
---

# Grok Video 全流程生成器

> 给 Grok Imagine 写可粘贴提示词。用户在 Grok App / grok.com 里自已点生成时，只做 Step 1–2，不要要求 API Key，不要跑本目录 CLI。

## Grok App 模式（默认）

用户说「我用的就是 Grok」时走这条：

1. 输出一段可直接粘贴的中文或中英提示词。
2. 图生视频时先锁身份，再写动作时间线，最后单独写 `Sound:`。
3. 不要写即梦 `@图片1` / `@音频1`。Grok 没有这个引用语法。
4. 不要承诺唱出受版权保护的原曲。Grok 会自编旋律；原曲只能后期贴。
5. 图生视频提示词只写「画面里会变的东西」，外貌交给参考图。

### Imagine 提示词骨架

```
Preserve the reference image subject's facial identity, hairstyle, outfit and scene. Do not change the face.

[0-2s] ...
[2-8s] ...
[8-15s] ...

Camera: slow push-in, no cut.
Keep the held prop in the same hand. No extra fingers. No on-screen text.

Sound: [环境声 + 人声语气。不要点名受版权保护的具体歌曲]。
```
