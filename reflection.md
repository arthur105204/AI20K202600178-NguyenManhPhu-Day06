# Individual reflection — Nguyễn Mạnh Phú (AI20K202600178)

## 1. Role
UX Engineer. Phụ trách thiết kế user flow và UI cho 2 feature chính: Deep Extraction (bảng synthesis) và Claim Verification; đảm bảo yếu tố trust/grounding và correction loop trong giao diện.

## 2. Đóng góp cụ thể
- Thiết kế **User Stories 4 paths** cho **2 features** (Happy / Low-confidence / Failure / Correction) và viết vào `spec-final.md` (phần 2).
- Thiết kế UI cho **bảng so sánh (matrix/workstation)**: 4 cột core (Methodology/Model, Dataset Used, Key Findings, Limitations) cùng cách hiển thị `N/A` theo nguyên tắc precision-first.
- Thiết kế các điểm **trust** trong UI: `source_quote` (evidence), nút **src check** mở link Semantic Scholar, và luồng **edit cell → Apply** để tạo learning signal cho data flywheel.
- Đóng góp vào demo flow: sắp xếp thứ tự thao tác để show được "query → search → bảng → evidence → src check → edit" trong thời gian ngắn.

## 3. SPEC mạnh/yếu
- **Mạnh nhất:** Trust + correction được thiết kế rõ trong user stories — UI luôn có evidence/src check, không chắc thì hiện N/A, user sửa được ngay trên cell và correction được log lại. Điều này giúp researcher không bao giờ phải "tin mù" vào output của AI.
- **Yếu nhất:** Claim Verification end-to-end chưa hoàn chỉnh trên UI — spec ghi rõ "as-built" chỉ có API, frontend chưa có màn hình verify chuyên dụng. Ngoài ra, mức grounding hiện tại quote theo hàng/paper, chưa tách quote riêng cho từng cell nên việc phát hiện mismatch chưa thật nhanh.

## 4. Đóng góp khác
- Phối hợp với engineer (Linh) để chốt **hình dạng data/UI contract** cho bảng extraction: 4 cột, rule N/A, payload khi edit cell (paper_id, field, original_value, corrected_value, timestamp).
- Review và chỉnh sửa `demo-script.md` để đảm bảo demo "live-friendly": thao tác ít bước, show được điểm trust trong thời gian ngắn.

## 5. Điều học được
Trong sản phẩm AI cho nghiên cứu, **UX trust = product requirement**: nếu không có evidence/src check thì user không thể biết AI sai và rất dễ "cite sai ngữ cảnh" — đây là vấn đề academic integrity nghiêm trọng. Thiết kế UI theo **precision-first** (thiếu thông tin thì hiện N/A thay vì bịa) nghe có vẻ "xấu" vì bảng nhiều ô trống, nhưng thực ra làm tool đáng tin hơn và giảm rủi ro cho researcher. Metric không chỉ là chuyện kỹ thuật mà là quyết định sản phẩm.

## 6. Nếu làm lại
- Sẽ test sớm hơn với 3–5 user thật (sinh viên đang làm thesis): họ cần cột nào nhất, cách đọc evidence thế nào, và ngưỡng "N/A nhiều quá" là bao nhiêu thì mất giá trị — những câu hỏi này nên được trả lời từ ngày đầu thay vì giả định.
- Sẽ đẩy nhanh UI cho Claim Verification (ít nhất 1 màn hình verify có evidence_quote + 3 mức status) để khi demo được "2 features" đầy đủ.

## 7. AI giúp gì / AI sai gì
- **Giúp:** dùng AI để brainstorm nhanh các biến thể UI cho "evidence + src check + edit" và viết microcopy ngắn gọn (ví dụ: cảnh báo "AI chỉ đọc abstract", ý nghĩa N/A). Cũng dùng AI để generate nhanh bộ user stories 4 paths — tiết kiệm thời gian viết spec đáng kể.
- **Sai/mislead:** Khi nhóm dùng AI để vẽ kịch bản test, đặt metrics/eval threshold và tính ROI, AI đưa ra các con số (ví dụ: extraction accuracy >= 85%, tiết kiệm 75 giờ/tháng) nhưng thiếu căn cứ — không trích nguồn, không giải thích assumption đằng sau. Nhóm phải prompt lại nhiều lần, yêu cầu AI ghi rõ nguồn cụ thể cho từng con số và cuối cùng vẫn cần con người xác thực lại toàn bộ vì AI không thể tự bịa ra số liệu đáng tin. Bài học: AI hỗ trợ draft nhanh nhưng output định lượng luôn cần người kiểm chứng và bổ sung nguồn.
