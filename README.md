# Arrumo Higgsfield Plugin

The default Higgsfield adapter for generated video assets.

`video-generation.json` describes Higgsfield's Kling 3.0 Standard text-to-video
endpoint with the [Plugin SDK video adapter](https://github.com/aidevs-pt/arrumo-plugin-sdk#describe-a-video-generation-adapter).
Arrumo submits the prompt, ratio (16:9, 9:16 or 1:1) and length (3 to 15
seconds, silent), polls the job, downloads the finished MP4 and adds it to the
workspace assets. Creators and agents ask for clips from **Assets › Generate ›
Video clip** or the `generate_library_video` operation.

## Key

Create an API key in the Higgsfield Cloud console and paste it into the plugin's
**Higgsfield API key** setting as `KEY_ID:KEY_SECRET`. Arrumo keeps it in the
system vault and sends it only to `api.higgsfield.ai`. Each clip uses your
Higgsfield credits; a job fails with `not_enough_credits` when the account is
empty.

## Release

Package with the SDK, including the adapter:

```sh
python3 ../plugin-sdk/tools/package_plugin.py . higgsfield.zip --include video-generation.json
```

## Icon and trademarks

`icon.svg` shows Higgsfield AI's logo so creators recognise the service this plugin connects to. Higgsfield and its logo are trademarks of Higgsfield AI; the manifest's `iconNotice` says so wherever Arrumo shows the icon. The logo is not covered by this repository's license, and this plugin is not affiliated with or endorsed by Higgsfield AI. The SVG is a square without rounded corners; Arrumo rounds it. If Higgsfield AI asks, replace the logo with a generic symbol and remove `iconNotice`.
