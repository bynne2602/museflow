# 26Flow

**26Flow** is a visual workflow extension for creating images and videos with your signed-in [Muse.ai](https://muse.ai) session. Build workflows by connecting nodes on a canvas, generate media, and arrange video clips on a timeline.

[Tiếng Việt](#tieng-viet) · [English](#english)

<a id="english"></a>

## Screenshots / Ảnh giao diện

### Demo video

[▶ Watch the 26Flow demo video (MP4)](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09%2011-17-18.mp4)

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

---

## Tiếng Việt

<a id="tieng-viet"></a>

**26Flow** là tiện ích mở rộng tạo quy trình trực quan bằng phiên Muse.ai bạn đã đăng nhập. Bạn có thể nối các node trên canvas, tạo ảnh/video và sắp xếp clip video trên timeline.

### Video demo

[▶ Xem video demo 26Flow (MP4)](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09%2011-17-18.mp4)

### Tính năng

- **Canvas node:** thêm, di chuyển, nối, chọn nhiều và sắp xếp node; phóng to/thu nhỏ, kéo canvas và mở thao tác bằng menu chuột phải.
- **Công cụ prompt:** tạo prompt, negative prompt, nối thêm hoặc gộp văn bản; hỗ trợ nối nhiều nguồn prompt ở các cổng phù hợp.
- **Quy trình ảnh:** đưa ảnh vào, kết nối nhiều ảnh tham chiếu, tạo ảnh, đổi kích thước và xem trước kết quả.
- **Quy trình video:** tạo clip, tùy chọn dùng frame cuối của clip trước làm ảnh tham chiếu mở đầu để giữ tính liên tục.
- **Timeline:** thêm và sắp xếp clip, đặt thời lượng, xem trước chuỗi clip và xuất video đã ghép định dạng WebM nếu trình duyệt hỗ trợ.
- **Script → Nodes:** chuyển kịch bản chia cảnh thành các node ảnh/video đã nối và timeline theo thứ tự.
- **Tệp workflow:** chọn **Save workflow** để tải workflow dạng JSON có thể dùng lại, rồi chọn **Import workflow** để mở lại. Media đầu vào và media đã tạo sẽ được nhúng nếu có thể; media từ xa không truy cập được sẽ giữ liên kết gốc.
- **Tự lưu cục bộ:** nút **Save** và tự động lưu giữ workflow hiện tại trong bộ nhớ extension trên trình duyệt.

### Yêu cầu

- Trình duyệt nền Chromium có hỗ trợ extension Manifest V3.
- Đăng nhập Muse.ai và mở trang chat Muse.ai trong lúc tạo nội dung.
- Tài khoản và giao diện Muse.ai cần hỗ trợ chức năng bạn muốn dùng. Tỷ lệ ảnh, âm thanh và khả năng tạo video phụ thuộc vào Muse.ai.

26Flow kết nối Muse.ai thông qua page bridge của extension. Ứng dụng không dùng muse2api, backend tạo nội dung riêng, API key, Docker hay bước build bằng npm. Khi chạy workflow, prompt và ảnh tham chiếu đã chọn sẽ được gửi tới Muse.ai.

### Cài đặt

1. Tải hoặc clone repository này và giải nén vào một thư mục cố định.
2. Mở trang quản lý extension của trình duyệt (Chrome: `chrome://extensions`).
3. Bật **Developer mode (Chế độ nhà phát triển)**.
4. Chọn **Load unpacked (Tải tiện ích đã giải nén)** và trỏ tới thư mục có file `manifest.json`.
5. Mở Muse.ai, đăng nhập và vào trang chat.
6. Mở **26Flow** và kiểm tra trạng thái phiên Muse.

#### Cập nhật

Thay các file dự án bằng phiên bản mới, sau đó nhấn **Reload (Tải lại)** ở trang quản lý extension. Tải lại cả tab Muse.ai để cập nhật bridge của extension.

### Bắt đầu nhanh

1. Thêm node **Prompt** và nhập nội dung.
2. Thêm node **Generate Image** hoặc **Generate Video**.
3. Kéo cổng output của Prompt sang cổng prompt của node tạo ảnh/video. Nối thêm ảnh tham chiếu hoặc input khác nếu cần.
4. Chọn thông số và nhấn **Run Image** hoặc **Run Video** trên node, hoặc chạy toàn workflow từ thanh công cụ.
5. Nối kết quả tới node **Preview**. Với video, thêm các clip vào **Timeline**, sắp xếp thứ tự rồi xem trước hoặc xuất video.

Để tạo node từ kịch bản, chọn **Script → Nodes**, dán nội dung và tạo workflow. Tiêu đề cảnh có thể theo dạng `CẢNH 1 (0:00–0:07): Tên cảnh`, cùng các trường `Prompt ảnh`, `Prompt video` và `Audio` nếu có.

### Dữ liệu và quyền truy cập

Workflow và media lưu cục bộ được giữ trong bộ nhớ extension trên thiết bị. Khi chạy workflow, 26Flow gửi prompt và ảnh tham chiếu liên quan tới Muse.ai thông qua phiên bạn đã đăng nhập. Extension cần quyền lưu trữ và truy cập tab để lưu workflow, kết nối với Muse.ai; extension không tạo tài khoản 26Flow hay máy chủ sinh nội dung riêng.

### Khắc phục sự cố

- **Không nhận phiên Muse:** đăng nhập Muse.ai, giữ trang chat đang mở, sau đó tải lại 26Flow và tab Muse.ai.
- **Không bắt đầu tạo hoặc không thấy media:** kiểm tra trang và phiên Muse.ai rồi thử lại. Muse.ai có thể thay đổi giao diện hoặc luồng tạo nội dung, khi đó extension cần được cập nhật.
- **Muse từ chối tạo cảnh:** 26Flow nhận diện lời từ chối, kể cả phản hồi tiếng Việt báo không tạo được hoặc đề nghị tạo bản tương đương, rồi tự thử lại cảnh đó một lần bằng prompt thay thế an toàn gần nhất. Không cần chờ xác nhận. Lần thử lại giữ vai trò của cảnh trong kịch bản và các thiết lập; Muse.ai vẫn quyết định nội dung có được tạo hay không.
- **Không xuất được timeline:** dùng trình duyệt có hỗ trợ `MediaRecorder` và canvas capture. Định dạng xuất là WebM.
- **Kết quả không đúng thông số:** Muse.ai quyết định media đầu ra; dịch vụ có thể không luôn làm theo tỷ lệ ảnh, âm thanh hoặc tùy chọn video được yêu cầu.

### Giấy phép

Phân phối theo [giấy phép MIT](LICENSE). Bản quyền (c) 2026 26Flow contributors.
