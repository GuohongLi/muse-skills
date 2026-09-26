# muse-skills

Two self-built, shareable photo-retouching skills for AI assistants, co-created with freya. They follow the open [Agent Skills](https://agentskills.io) format (`SKILL.md` + `name`/`description` frontmatter), so any assistant that supports skills can load them.

两个自建、可分享的修图 skill，遵循开放的 Agent Skills 格式（`SKILL.md` + frontmatter），支持该格式的 AI 助手均可加载使用。

## Skills

### portrait-retouch（人像修图）
Professional portrait retouching workflow with automatic secondary composition. Trigger: user says 「人像修图」 and attaches a portrait photo. Flow: diagnose (quality + composition) → plan 1–4 compositions (face close-up / half-body / environmental / negative space) → retouch each with the assistant's image editing tool → verify → upscale to 2K → deliver. Default style: Haimati / Korean fresh look; alternatives: Japanese, Western, classical Chinese. Hard rules: keep real skin texture, eyes 100% sharp, never alter facial features, zero face distortion.

### vcg-retouch（视觉中国修图）
Stock-photo-grade retouching to Visual China Group (VCG) quality standards, with automatic secondary composition. Trigger: user says 「修图」/「视觉中国修图」 and attaches a photo. Flow: diagnose → plan 1–4 recompositions → retouch → verify → upscale to 2K if needed → deliver. Auto-upscale rule: if the longest side is under 2560px, run one upscale pass (AI upscaler preferred, high-quality interpolation fallback).

## Examples / 示例
Before/after pairs in [`examples/`](examples/) — four sets retouched with `vcg-retouch` from real user photos （宝塔夜景全景/长焦、瀑布全景/长焦）, each with a note on what was diagnosed and fixed. The telephoto versions also demonstrate the skill's secondary-composition capability （同一张原图裁出不同版本）.

## Requirements / 环境要求
The assistant needs an **image generation/editing capability** (able to edit or redraw a photo from instructions). An AI upscaler (e.g. Real-ESRGAN) is optional; Lanczos/bicubic interpolation works as fallback.

助手需要具备**图像生成/编辑能力**；超分工具（如 Real-ESRGAN）可选，没有可用高质量插值放大兜底。

## Install / 安装

**Claude Code / any assistant supporting the Agent Skills format:**

```bash
git clone https://github.com/GuohongLi/muse-skills.git
cp -r muse-skills/portrait-retouch ~/.claude/skills/
cp -r muse-skills/vcg-retouch ~/.claude/skills/
```

**Other agents (e.g. Codex):** these agents don't natively load `SKILL.md`, but the files are plain Markdown — read them and follow the workflow, or paste the relevant section into your agent's instructions file (e.g. `AGENTS.md`). The workflows, quality standards and hard rules transfer as-is; only the image-tool invocation needs mapping to your agent's own image tools.

**其他助手（如 Codex）：** 原生不支持 `SKILL.md`，但文件本身就是 Markdown，直接照读执行即可，或把相关章节粘贴进你的指令文件（如 `AGENTS.md`）。工作流、画质标准、硬规则通用，只需把"调用图像工具"那一步映射成你助手的图像能力。

## Usage / 用法
- 说「人像修图」并附上人像照片 → portrait-retouch 触发
- 说「修图」/「视觉中国修图」并附上照片 → vcg-retouch 触发

## License
MIT — free to use, modify and share. 详见 [LICENSE](LICENSE)。
