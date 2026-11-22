# Arrumo Higgsfield Plugin

The default Higgsfield adapter for generated video assets.

`video-generation.json` is a schema 2 [Plugin SDK video adapter](https://github.com/aidevs-pt/arrumo-plugin-sdk#describe-a-video-generation-adapter)
with three models, chosen in the plugin's **Video model** setting or per clip:

| Model | Without references | With references | Length |
| --- | --- | --- | --- |
| `kling-3.0-std` (default) | Text to video | One image to animate | 3–15 s |
| `kling-3.0-pro` | Text to video | One image to animate | 3–15 s |
| `seedance-2.0` | Not available | 1–9 images and up to 3 videos, or 1–3 videos | 4–15 s |

Arrumo submits the prompt, ratio (16:9, 9:16 or 1:1; an animated image keeps
its own shape) and length, silent. Reference files are workspace assets: Arrumo
uploads each through Higgsfield's presigned upload and passes the returned
address. It polls the job, downloads the finished MP4 and adds it to the
workspace assets. Creators pick models and references in **Assets › Generate ›
Video clip**; agents use `list_video_models` and `generate_library_video`.

## Key

Create an API key in the [Higgsfield console](https://console.higgsfield.ai/) and paste it into the plugin's
**Higgsfield API key** setting as `KEY_ID:KEY_SECRET`. Arrumo keeps it in the
system vault and sends it only to `api.higgsfield.ai`; reference uploads go to
the presigned storage address without it. Each clip uses your
Higgsfield credits; a job fails with `not_enough_credits` when the account is
empty.

## Release

Package with the SDK, including the adapter:

```sh
python3 ../plugin-sdk/tools/package_plugin.py . higgsfield.zip --include video-generation.json
```

## Icon and trademarks

`icon.svg` shows Higgsfield AI's logo so creators recognise the service this plugin connects to. Higgsfield and its logo are trademarks of Higgsfield AI; the manifest's `iconNotice` says so wherever Arrumo shows the icon. The logo is not covered by this repository's license, and this plugin is not affiliated with or endorsed by Higgsfield AI. The SVG is a square without rounded corners; Arrumo rounds it. If Higgsfield AI asks, replace the logo with a generic symbol and remove `iconNotice`.
