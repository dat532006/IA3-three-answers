# AI-LOG.md

AI-assisted draft — pending student review.

## 2026-11-04 — IA#3: phân tích tĩnh và soạn prediction

Tool: Codex (ứng dụng desktop). Thông tin phiên mô tả agent dựa trên GPT-6; chưa có định danh backend/phiên bản model cụ thể được kiểm chứng. Dùng công cụ đọc tệp/lệnh PowerShell, Git chỉ đọc và skill PDF để trích chữ/render/đọc rubric; dùng công cụ chỉnh tệp cho đúng hai báo cáo được cho phép. Không dùng sub-agent.

Asked for: Đọc rubric, mẫu AI log, brief/README và source A/B/C cùng ngữ cảnh thực thi; kiểm tra baseline; phân tích tĩnh, giải thích cơ chế, soạn prediction với 27 hàng và kế hoạch kiểm chứng, rồi bàn giao cho người học.

Kept: Chưa được người học đánh giá/xác nhận; chưa có quyết định giữ nguyên nội dung AI.

Changed: Chưa được người học đánh giá/xác nhận; chưa có sửa đổi của người học hoặc kết quả chạy chứng minh cần sửa nhận định.

Rejected: Chưa được người học đánh giá/xác nhận; chưa có nhận định hay đề xuất bị người học từ chối để ghi nhận.

By hand: Chưa được người học đánh giá/xác nhận; chưa có bằng chứng về phần nội dung báo cáo do người học tự viết trong phiên này.

Kết quả thực sự tạo: `VERDICTS.md` và `AI-LOG.md` tại workspace. Trước phiên chưa có hai tệp này. Bản VERDICTS có nguồn/commit/dòng mã, ba bảng gồm tổng cộng 27 prediction, phân tích độc lập A/B/C, concurrency, rủi ro ngoài ma trận, verdict sơ bộ và phần runtime giữ NOT_TESTED. Bản nháp dự kiến A fix do hàng 2, B fix do hàng 6 và 8, C keep có điều kiện; đây là suy luận của AI, chưa phải quyết định người học hoặc kết quả kiểm thử.

Baseline và rà soát: HEAD là `c1f62e8207f7d0f42f3f91d0b106e1bb3cceacad` (`starter`), working tree sạch trước khi tạo bản nháp. Đã đọc tài liệu/source và đối chiếu Git; rà lại nội dung hai báo cáo, số hàng và diff. Không tìm thấy bằng chứng kiểm thử có sẵn trong các tệp/lịch sử được kiểm tra; không thể suy rằng người học chưa từng chạy ở nơi khác. Ảnh PDF chỉ là bản render tài liệu trong thư mục tạm ngoài repository, không phải evidence runtime.

Phạm vi đã thực hiện: chỉ đọc source/Git và tạo/rà soát đúng hai tệp báo cáo. Chưa chạy ứng dụng/server, browser test, TypeScript checker, build, formatter; không cài dependency. Chưa sửa source, chưa add/commit/push hoặc đổi index/refs/history; không tạo evidence/, báo cáo khác, ZIP hoặc nộp bài. Việc đọc/render PDF và kiểm đếm cấu trúc Markdown không phải kiểm thử ứng dụng.

Trạng thái bàn giao: **pending student review**. Người học có thể Chấp nhận / Sửa và nêu lý do / Chưa đồng ý hoặc cần giải thích. Chưa có prediction commit mới. Chấp nhận nội dung không tự cấp quyền commit/push; kiểm thử chỉ bắt đầu khi người học xác nhận rõ prediction đã commit trước testing và tiếp tục giao nhiệm vụ kiểm thử.

Giới hạn khai báo: đây là một entry cho phiên hỗ trợ soạn prediction, không phải review độc lập chính thức ở bước ASSISTANT-REVIEW. Không ghi phiên trước, quan sát, lỗi assistant bị kiểm thử bắt được, regression hoặc quyết định Changed/Rejected khi chưa có bằng chứng; không tự chấm điểm.
