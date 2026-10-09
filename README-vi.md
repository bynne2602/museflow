# 26Flow

[English](README.md)

**Tải nhanh:** [Tải MuseFlow-extension.zip](https://github.com/bynne2602/museflow/releases/latest/download/MuseFlow-extension.zip) · Không cần cài npm hoặc build.

**26Flow** là tiện ích mở rộng tạo quy trình trực quan bằng phiên Muse.ai bạn đã đăng nhập. Bạn có thể nối các node trên canvas, tạo ảnh/video và sắp xếp clip video trên timeline.

## Ảnh giao diện

### Canvas workflow và Muse.ai

![Canvas 26Flow kết nối với phiên Muse.ai](docs/screenshots/26flow-workflow-canvas.png)

### Xem trước timeline

![26Flow phát một cảnh video trong cửa sổ xem trước](docs/screenshots/26flow-timeline-preview.png)

### Chỉnh sửa timeline

![Timeline 26Flow với thứ tự clip, ảnh xem trước và thời lượng](docs/screenshots/26flow-timeline-editor.png)

### Video demo

[![Xem MuseFlow: tạo ảnh, tạo video và ghép cảnh bằng Muse.ai](https://img.youtube.com/vi/w7mJwTJyzKw/maxresdefault.jpg)](https://www.youtube.com/watch?v=w7mJwTJyzKw)

[▶ Xem trên YouTube](https://www.youtube.com/watch?v=w7mJwTJyzKw) · [Tải video demo MP4](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09.11-17-18.mp4)

### Tính năng

- **Canvas node:** thêm, di chuyển, nối, chọn nhiều và sắp xếp node; phóng to/thu nhỏ, kéo canvas và mở thao tác bằng menu chuột phải.
- **Công cụ prompt:** tạo prompt, negative prompt, nối thêm hoặc gộp văn bản; hỗ trợ nối nhiều nguồn prompt ở các cổng phù hợp.
- **Quy trình ảnh:** đưa ảnh vào, kết nối nhiều ảnh tham chiếu, tạo ảnh, đổi kích thước và xem trước kết quả.
- **Quy trình video:** tạo clip, tùy chọn dùng frame cuối của clip trước làm ảnh tham chiếu mở đầu để giữ tính liên tục.
- **Timeline:** thêm và sắp xếp clip, đặt thời lượng, xem trước chuỗi clip; xuất WebM hoặc ghép toàn bộ timeline thành MP4 (H.264) bằng FFmpeg được đóng gói trong extension. MP4 được xử lý ngay trên máy.
- **Script → Nodes:** chuyển kịch bản chia cảnh thành các node ảnh/video đã nối và timeline theo thứ tự.
- **Tệp workflow:** chọn **Save workflow** để tải workflow dạng JSON có thể dùng lại, rồi chọn **Import workflow** để mở lại. Media đầu vào và media đã tạo sẽ được nhúng nếu có thể; media từ xa không truy cập được sẽ giữ liên kết gốc.
- **Tự lưu cục bộ:** nút **Save** và tự động lưu giữ workflow hiện tại trong bộ nhớ extension trên trình duyệt.

### Yêu cầu

- Trình duyệt nền Chromium có hỗ trợ extension Manifest V3.
- Đăng nhập Muse.ai và mở trang chat Muse.ai trong lúc tạo nội dung.
- Tài khoản và giao diện Muse.ai cần hỗ trợ chức năng bạn muốn dùng. Tỷ lệ ảnh, âm thanh và khả năng tạo video phụ thuộc vào Muse.ai.

26Flow kết nối Muse.ai thông qua page bridge của extension. Ứng dụng không dùng muse2api, backend tạo nội dung riêng, API key, Docker hay bước build bằng npm. Khi chạy workflow, prompt và ảnh tham chiếu đã chọn sẽ được gửi tới Muse.ai. Chức năng xuất MP4 dùng engine FFmpeg WebAssembly được đóng gói cùng extension và xử lý video cục bộ trên máy.

### Cài đặt

1. Tải [MuseFlow-extension.zip](https://github.com/bynne2602/museflow/releases/latest/download/MuseFlow-extension.zip) từ GitHub Releases rồi giải nén vào một thư mục cố định. Nếu chưa có gói phát hành, bạn có thể [tải ZIP repository](https://github.com/bynne2602/museflow/archive/refs/heads/main.zip).
2. Mở trang quản lý extension của trình duyệt (Chrome: `chrome://extensions`).
3. Bật **Developer mode (Chế độ nhà phát triển)**.
4. Chọn **Load unpacked (Tải tiện ích đã giải nén)** và trỏ tới thư mục có file `manifest.json`.
5. Mở Muse.ai, đăng nhập và vào trang chat.
6. Mở **26Flow** và kiểm tra trạng thái phiên Muse.

Không cần cài npm hoặc chạy bước build. ZIP tải về có mã nguồn extension và các file FFmpeg cục bộ đi kèm. Khi chọn **Load unpacked**, hãy chọn thư mục sau giải nén có chứa trực tiếp file `manifest.json`.

### Tải gói ZIP cài sẵn

Gói Release chỉ chứa các file cần để chạy extension và thông báo giấy phép liên quan. Cần giải nén trước, sau đó chọn thư mục chứa `manifest.json` bằng **Load unpacked**; không chọn trực tiếp file ZIP.

#### Cập nhật

Thay các file dự án bằng phiên bản mới, sau đó nhấn **Reload (Tải lại)** ở trang quản lý extension. Tải lại cả tab Muse.ai để cập nhật bridge của extension.

## Mở MuseFlow và Muse.ai cạnh nhau

Để dễ thao tác và theo dõi quá trình tạo nội dung, bạn có thể hiển thị canvas MuseFlow và khung chat Muse.ai cùng lúc:

1. Mở trang chat Muse.ai trong một cửa sổ trình duyệt.
2. Nhấn biểu tượng extension MuseFlow để mở canvas trong tab mới. Kéo tab MuseFlow ra khỏi thanh tab để tách thành cửa sổ riêng.
3. Trên Windows, chọn cửa sổ MuseFlow rồi nhấn **Windows + phím mũi tên trái**. Chọn cửa sổ Muse.ai rồi nhấn **Windows + phím mũi tên phải**. Bạn cũng có thể kéo từng cửa sổ sát mép trái hoặc mép phải màn hình.
4. Giữ cả hai trang mở khi tạo nội dung để theo dõi node đang chạy trong MuseFlow và phản hồi tạo nội dung trong Muse.ai.

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
- **Xuất timeline bị lỗi:** tải lại extension rồi thử lại. MP4 dùng engine FFmpeg đi kèm; WebM dùng `MediaRecorder` và canvas capture của trình duyệt.
- **Kết quả không đúng thông số:** Muse.ai quyết định media đầu ra; dịch vụ có thể không luôn làm theo tỷ lệ ảnh, âm thanh hoặc tùy chọn video được yêu cầu.

### Giấy phép

Mã nguồn gốc MuseFlow được ghi nhận theo [giấy phép MIT](LICENSE). Engine FFmpeg WebAssembly đi kèm theo GPL-2.0-or-later, nên khi phân phối toàn bộ extension cũng phải tuân thủ các yêu cầu của GPL. Xem [thông báo giấy phép bên thứ ba](THIRD_PARTY_NOTICES.md) và các tệp giấy phép đi kèm.
