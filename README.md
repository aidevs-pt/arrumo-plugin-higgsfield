<p align="center">
  <img src="icon.svg" width="88" height="88" alt="">
</p>

<h1 align="center">Higgsfield for Arrumo AI Video Editor</h1>

<p align="center">Generate video clips and images with 57 video and 19 image models through Higgsfield, from text, frames or references.</p>

<p align="center">
  <a href="LICENSE"><img alt="License: AGPL-3.0" src="https://img.shields.io/badge/license-AGPL--3.0-2337B4"></a>
  <img alt="Bundled with Arrumo" src="https://img.shields.io/badge/bundled%20with-Arrumo-2337B4">
  <a href="https://www.aidevs.pt/tools/arrumo/docs/plugins/higgsfield/video-and-images"><img alt="Docs in English, Spanish and Portuguese" src="https://img.shields.io/badge/docs-EN%20%C2%B7%20ES%20%C2%B7%20PT-111"></a>
</p>

[![Arrumo + Higgsfield: a launch film made entirely in Arrumo](media/arrumo-higgsfield.gif)](https://youtu.be/a8z9Aql6qPg)

<p align="center"><sub>Every clip and image in this video was generated with this plugin, and Arrumo made the whole video.</sub></p>

This plugin ships with [Arrumo AI Video Editor](https://github.com/aidevs-pt/arrumo-video-editor), the free, open-source desktop app where an AI agent writes, designs, voices and cuts your videos and you approve every step. It comes installed with Arrumo; turn it on or off in **Settings › Plugins**.

## Guides

- **Video clips and images**: [English](https://www.aidevs.pt/tools/arrumo/docs/plugins/higgsfield/video-and-images) · [Español](https://www.aidevs.pt/es/tools/arrumo/docs/plugins/higgsfield/video-and-images) · [Português](https://www.aidevs.pt/pt/tools/arrumo/docs/plugins/higgsfield/video-and-images)

## How it works

`video-generation.json` and `image-generation.json` are schema 3
[Plugin SDK adapters](https://github.com/aidevs-pt/arrumo-plugin-sdk#reference)
covering 57 video models (Kling 4.0 and 4.0 Flash, Kling 3.0, 2.6, 2.5, O3
and Omni, Seedance 2.0 and 2.5, MAGI-2, Genjutsu and Genjutsu Light, Happy
Horse, Wan 3.0, 2.7 and 2.6, Hailuo 2.3, PixVerse V6, Cinema Studio 4.0,
LTX-2.5, MiniMax H3 Highspeed and Lite, and Grok Imagine Video) and 19 image
models (Qwen Image 3, Seedream 5.0 Pro, Kling Image 4.0, SOUL, Grok Image 2.0,
Ideogram 4.0, Z-Image Turbo, Recraft V4.1, Marketing Studio, Ads Studio, and
the Product Shots, Graphic Ads and Marketplace Design workflows). Each model has a label and a best-for line in English, Spanish and
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

## Contributing

Contributions are welcome: read [CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md). Report security problems privately as described in [SECURITY.md](SECURITY.md).

## License

Copyright © 2026 DEVS.AI UNIPESSOAL LDA. Licensed under the [GNU Affero General Public License v3.0](LICENSE). Built by [DEVS AI](https://aidevs.pt), who make custom AI solutions for companies.
