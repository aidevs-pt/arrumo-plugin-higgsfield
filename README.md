# Arrumo Higgsfield Plugin

The default Higgsfield adapters for generated video and image assets.

## Guide

[English](https://github.com/aidevs-pt/arrumo-docs/blob/main/content/docs/en/plugins/higgsfield/video-and-images.md) · [Español](https://github.com/aidevs-pt/arrumo-docs/blob/main/content/docs/es/plugins/higgsfield/video-and-images.md) · [Português](https://github.com/aidevs-pt/arrumo-docs/blob/main/content/docs/pt/plugins/higgsfield/video-and-images.md)

`video-generation.json` and `image-generation.json` are schema 3
[Plugin SDK adapters](https://github.com/aidevs-pt/arrumo-plugin-sdk#reference)
covering 45 video models (Kling 3.0, 2.6, 2.5, O3 and Omni, Seedance 2.0 and
2.5, Genjutsu, Happy Horse, Wan 3.0, 2.7 and 2.6, Hailuo 2.3, PixVerse V6,
Cinema Studio 4.0, LTX-2.5, MiniMax H3 and Grok Imagine Video) and 15 image
models (Qwen Image 3, SOUL, Grok Image 2.0, Ideogram 4.0, Z-Image Turbo,
Recraft V4.1, Marketing Studio and Ads Studio). Each model has a label and a best-for line in English, Spanish and
Portuguese, which the guide lists. The **Video model** and **Image model**
settings pick the workspace defaults; creators and agents can choose any model
per asset.

Arrumo picks the variant of a model that fits the references attached (text,
first frame, first and last frames, reference images and videos, or a clip to
edit or extend), uploads each reference through Higgsfield's presigned upload,
polls the job and adds the finished MP4 or image to the workspace assets.
Generated audio stays off, so narration and music come from the edit.
Workflows that need Higgsfield presets or trained IDs are not included, nor
text-to-video for Hailuo 2.3 and Wan 2.6 (their APIs take no size) or PixVerse
V6 image-to-video.

## Key

Create an API key in the [Higgsfield console](https://console.higgsfield.ai/) and paste it into the plugin's
**Higgsfield API key** setting as `KEY_ID:KEY_SECRET`. Arrumo keeps it in the
system vault and sends it only to `api.higgsfield.ai`; reference uploads go to
the presigned storage address without it. Each clip and image uses your
Higgsfield credits; a job fails with `not_enough_credits` when the account is
empty.

## Release

Package with the SDK, including the adapter:

```sh
python3 ../plugin-sdk/tools/package_plugin.py . higgsfield.zip --include video-generation.json --include image-generation.json
```

## Icon and trademarks

`icon.svg` shows Higgsfield AI's logo so creators recognise the service this plugin connects to. Higgsfield and its logo are trademarks of Higgsfield AI; the manifest's `iconNotice` says so wherever Arrumo shows the icon. The logo is not covered by this repository's license, and this plugin is not affiliated with or endorsed by Higgsfield AI. The SVG is a square without rounded corners; Arrumo rounds it. If Higgsfield AI asks, replace the logo with a generic symbol and remove `iconNotice`.
