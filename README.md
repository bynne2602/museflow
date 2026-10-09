# 26Flow

**26Flow** is a visual workflow extension for creating images and videos with your signed-in [Muse.ai](https://muse.ai) session. Build workflows by connecting nodes on a canvas, generate media, and arrange video clips on a timeline.

[Tiếng Việt](README-vi.md)

**Quick install:** [Download MuseFlow-extension.zip](https://github.com/bynne2602/museflow/raw/refs/heads/main/downloads/MuseFlow-extension.zip) · No npm install or build step required.

## Screenshots

### Demo video

[![Watch MuseFlow: create images, generate videos, and assemble scenes with Muse.ai](https://img.youtube.com/vi/w7mJwTJyzKw/maxresdefault.jpg)](https://www.youtube.com/watch?v=w7mJwTJyzKw)

[▶ Watch on YouTube](https://www.youtube.com/watch?v=w7mJwTJyzKw) · [Download the MP4 demo](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09.11-17-18.mp4)

### Workflow canvas and Muse.ai

![26Flow workflow canvas connected to a Muse.ai session](docs/screenshots/26flow-workflow-canvas.png)

### Timeline preview

![26Flow playing a generated scene in the timeline preview panel](docs/screenshots/26flow-timeline-preview.png)

### Timeline editor

![26Flow timeline with ordered clips, thumbnails, and duration controls](docs/screenshots/26flow-timeline-editor.png)

## Features

- **Visual node canvas:** add, move, connect, multi-select, and arrange workflow nodes. Hold **Alt** while dragging to copy a node or selection with its incoming connections; press **Ctrl+Z** to undo the last canvas or workflow edit. Press **G** and drag on the canvas to draw a group region; press **T** to add a freeform text note directly to the canvas. Notes can be edited, moved, and saved with the workflow. Group regions are saved with the workflow. Pan and zoom the canvas, and use the context menu for node actions.
- **Prompt tools:** create prompts, negative prompts, append or merge text; Text Merge accepts multiple text sources on one input and joins them in connection order with a configurable separator.
- **Image workflows:** provide image inputs and references, generate images, resize outputs, and preview connected media.
- **Video workflows:** generate video clips, optionally use the preceding timeline clip's end frame as a continuity reference, and preview connected video.
- **Timeline:** add and reorder clips, set clip durations, preview the sequence, export WebM, or assemble the full timeline as MP4 (H.264) with the bundled local FFmpeg engine. MP4 processing stays on your device.
- **Script to nodes:** turn a scene-based script into connected image/video nodes and an ordered timeline.
- **Workflow files:** use **Save workflow** to download a reusable JSON file and **Import workflow** to restore it later. Generated and input media are embedded when available; inaccessible remote media remains linked to its original URL.
- **Local workflow saving:** **Save** and autosave keep the current workflow in the extension's browser storage.

## Requirements

- A Chromium-based browser with Manifest V3 extension support.
- An active, signed-in Muse.ai session. Keep the Muse.ai chat page open while generating media.
- Muse.ai account and page features that support the requested generation. Aspect ratio, audio, and video availability depend on Muse.ai.

26Flow communicates with Muse.ai through the extension's page bridge. It does not use muse2api, a separate generation backend, API keys, Docker, or an npm build step. Prompts and selected reference images are submitted to Muse.ai when you run a generation. Timeline MP4 export uses the FFmpeg WebAssembly engine packaged with the extension and processes video locally.

## Install

1. Download [MuseFlow-extension.zip](https://github.com/bynne2602/museflow/raw/refs/heads/main/downloads/MuseFlow-extension.zip) and extract it to a permanent folder. Alternatively, [download the repository ZIP](https://github.com/bynne2602/museflow/archive/refs/heads/main.zip).
2. Open your browser's extensions page (for Chrome, `chrome://extensions`).
3. Enable **Developer mode**.
4. Select **Load unpacked** and choose the folder containing `manifest.json`.
5. Open Muse.ai, sign in, and open its chat page.
6. Open **26Flow** and check the Muse session status.

There is no npm install or build step. The downloaded ZIP contains the extension source and bundled local FFmpeg files. Choose the extracted repository folder that directly contains `manifest.json` when using **Load unpacked**.

### Download a packaged ZIP

The packaged ZIP contains the extension, bundled FFmpeg files, and their required license notices. Extract it first, then select the folder containing `manifest.json` in **Load unpacked**. Do not select the ZIP file itself.

### Update

Replace the project files with the updated version, then select **Reload** on the browser extensions page. Reload the Muse.ai tab as well so its extension bridge is refreshed.

## View MuseFlow and Muse.ai side by side

For a clearer view while you work, keep the Muse.ai chat and the MuseFlow canvas visible at the same time:

1. Open the Muse.ai chat in one browser window.
2. Click the MuseFlow extension icon to open its canvas in a tab. Move that tab into a separate window by dragging it out of the tab strip.
3. In Windows, select the MuseFlow window and press **Windows key + Left Arrow**. Select the Muse.ai window and press **Windows key + Right Arrow**. You can also drag each window to the left or right edge of the screen.
4. Keep both pages open during generation so you can follow the active workflow node in MuseFlow and the generation response in Muse.ai.

## Quick start

1. Add a **Prompt** node and enter your prompt.
2. Add a **Generate Image** or **Generate Video** node.
3. Drag the prompt node's output to the generator's prompt input. Connect any reference image or other inputs you need.
4. Choose the output settings and click **Run Image** or **Run Video** on that node, or run the workflow from the toolbar.
5. Connect generated media to a **Preview** node. For video, add clips to the **Timeline**, arrange their order, and preview or export the sequence.

For a scene script, use **Script → Nodes**, paste the script, and create the workflow. Scene headings should use a format such as `CẢNH 1 (0:00–0:07): Scene title`, with fields such as `Prompt ảnh`, `Prompt video`, and optional `Audio`.

## Data and permissions

Workflows and locally stored media are kept in browser extension storage on your device. When you run a workflow, 26Flow submits the relevant prompt and reference media to Muse.ai through your signed-in session. The extension requests browser storage and tab access to save workflows and communicate with Muse.ai; it does not configure a separate 26Flow account or generation server.

## Troubleshooting

- **Muse session is unavailable:** sign in to Muse.ai, keep its chat page open, then reload 26Flow and the Muse.ai tab.
- **Generation does not start or media is missing:** check the Muse.ai page and session, then retry. Muse.ai may change its interface or generation behavior, which can require an extension update.
- **Muse declines a scene:** 26Flow detects refusal messages, including Vietnamese replies that say a scene cannot be created or offer to make an equivalent, and retries that scene once with a close, safer alternative prompt. It does not wait for confirmation. The retry keeps the scene's narrative role and settings; Muse.ai still determines whether the result can be generated.
- **Timeline export fails:** reload the extension and try again. MP4 uses the bundled FFmpeg engine; WebM uses browser `MediaRecorder` and canvas capture.
- **Output differs from requested settings:** Muse.ai controls the generated media; the requested aspect ratio, audio, and video options may not always be honored by the service.

## License

MuseFlow is licensed under the [GNU General Public License v2.0 or later (GPL-2.0-or-later)](LICENSE), matching the bundled FFmpeg core. The FFmpeg JavaScript wrapper remains MIT-licensed. See [third-party notices](THIRD_PARTY_NOTICES.md) and the included license texts.
