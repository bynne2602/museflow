# 26Flow

**26Flow** is a visual workflow extension for creating images and videos with your signed-in [Muse.ai](https://muse.ai) session. Build workflows by connecting nodes on a canvas, generate media, and arrange video clips on a timeline.

[Tiếng Việt](README-vi.md)

## Screenshots

### Demo video

[▶ Watch the 26Flow demo video (MP4)](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09.11-17-18.mp4)

### Workflow canvas and Muse.ai

![26Flow workflow canvas connected to a Muse.ai session](docs/screenshots/26flow-workflow-canvas.png)

### Timeline preview

![26Flow playing a generated scene in the timeline preview panel](docs/screenshots/26flow-timeline-preview.png)

### Timeline editor

![26Flow timeline with ordered clips, thumbnails, and duration controls](docs/screenshots/26flow-timeline-editor.png)

## Features

- **Visual node canvas:** add, move, connect, multi-select, and arrange workflow nodes. Pan and zoom the canvas, and use the context menu for node actions.
- **Prompt tools:** create prompts, negative prompts, append or merge text, and connect multiple prompt sources where supported.
- **Image workflows:** provide image inputs and references, generate images, resize outputs, and preview connected media.
- **Video workflows:** generate video clips, optionally use the preceding timeline clip's end frame as a continuity reference, and preview connected video.
- **Timeline:** add and reorder clips, set clip durations, preview the sequence, and export the stitched timeline as WebM when supported by the browser.
- **Script to nodes:** turn a scene-based script into connected image/video nodes and an ordered timeline.
- **Workflow files:** use **Save workflow** to download a reusable JSON file and **Import workflow** to restore it later. Generated and input media are embedded when available; inaccessible remote media remains linked to its original URL.
- **Local workflow saving:** **Save** and autosave keep the current workflow in the extension's browser storage.

## Requirements

- A Chromium-based browser with Manifest V3 extension support.
- An active, signed-in Muse.ai session. Keep the Muse.ai chat page open while generating media.
- Muse.ai account and page features that support the requested generation. Aspect ratio, audio, and video availability depend on Muse.ai.

26Flow communicates with Muse.ai through the extension's page bridge. It does not use muse2api, a separate generation backend, API keys, Docker, or an npm build step. Prompts and selected reference images are submitted to Muse.ai when you run a generation.

## Install

1. Download or clone this repository and extract it to a permanent folder.
2. Open your browser's extensions page (for Chrome, `chrome://extensions`).
3. Enable **Developer mode**.
4. Select **Load unpacked** and choose the folder containing `manifest.json`.
5. Open Muse.ai, sign in, and open its chat page.
6. Open **26Flow** and check the Muse session status.

### Update

Replace the project files with the updated version, then select **Reload** on the browser extensions page. Reload the Muse.ai tab as well so its extension bridge is refreshed.

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
- **Timeline export is unavailable:** use a browser that supports `MediaRecorder` and canvas capture. Export format is WebM.
- **Output differs from requested settings:** Muse.ai controls the generated media; the requested aspect ratio, audio, and video options may not always be honored by the service.

## License

Distributed under the [MIT License](LICENSE). Copyright (c) 2026 26Flow contributors.
