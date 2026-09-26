# muse-skills

Self-built skills for Muse, co-created with freya.

## Skills

### portrait-retouch （人像修图）
Professional portrait retouching workflow in the 海马体 / Korean-fresh style.
Trigger: say 「人像修图」 with a portrait photo.
Flow: diagnose → 1–4 composition plans (face close-up / half-body / environmental / negative-space) → retouch → verify → 2K upscale → deliver.
Hard rules: keep real skin texture (no plastic skin), eyes 100% sharp, never alter facial features, minimal liquify, zero face distortion on close-ups.

### vcg-retouch （视觉中国修图）
Stock-photo-grade retouching to Visual China Group (VCG) quality standards, with automatic secondary composition.
Trigger: say 「视觉中国修图」 or 「修图」 with a photo.
Flow: diagnose (incl. composition) → 1–4 recomposition plans → retouch → verify → deliver.
Auto-upscale rule: if the longest side of the source or auto-composed result is under 2560px, run one upscale pass (Real-ESRGAN preferred, PIL LANCZOS 2× fallback), re-verify, and note the method on delivery.
