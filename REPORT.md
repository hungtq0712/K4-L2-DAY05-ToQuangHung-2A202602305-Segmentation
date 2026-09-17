# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A0202602305
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: Opencv tools,AI feature detector

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task                     | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| ------------------------ | -------------------- | ---------------------: | --------------------------------: |
| easy_semantic            | easy_semantic.zip    |                   3/ 3 |                                20 |
| medium_instance          | medium_instance.zip  |                   3/ 3 |                                32 |
| hard_panoptic            | hard_panoptic.zip    |                  2 / 2 |                                30 |
| cp1_holes                | cp1_holes.zip        |                   1/ 1 |                                 3 |
| cp2_slice                | cp2_slice.zip        |                   1/ 1 |                                 3 |
| cp5_occlusion            | cp5_occlusion.zip    |                   1/ 1 |                                 3 |
| cp3_thin                 | cp3_thin.zip         |                  1 / 1 |                                 3 |
| cp4_curb                 | cp4_curb.zip         |                   1/ 1 |                                 3 |
| cp6_coverage             | cp6_coverage.zip     |                  1 / 1 |                                 3 |
| **Tổng tối đa** |                      |                        |                     **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh `000000181542.jpg` - Xe máy phía bên trái.
- Class và quy tắc tôi dùng để chọn biên: Lớp `motorcycle`. Quy tắc: Vẽ khít theo phần nhìn thấy của thân xe và bánh xe, loại trừ các phần bị che khuất bởi người ngồi trên xe (được gán lớp `person`).
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Có sử dụng AI Tools (AI feature detector) để hỗ trợ tìm biên nhanh hơn đối với các ô tô ở xa, sau đó tinh chỉnh lại bằng tay các điểm bị lệch ở vùng bóng râm.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Task `cp5_occlusion` / ảnh `000000336232.jpg` / chiếc xe bus bị che khuất.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: gộp-tách / biên.
- Bằng chứng tôi nhìn thấy: Ban đầu xuất dữ liệu không có annotation nào hoặc bị chia tách làm hai vùng rời rạc cho cùng một chiếc xe bus.
- Quy tắc và hành động sửa: Gộp chung 2 vùng bị che khuất thành một instance duy nhất theo đúng đặc tả của bài toán Occlusion.
- Sau sửa đã Save và export lại chưa? Đã lưu và xuất bản ZIP `cp5_occlusion.zip` hoàn tất.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí                                                                                    | Hai cách hiểu có thể                             | Quy tắc/chứng cứ            | Quyết định hoặc câu hỏi cho coach                                       |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------- | ------------------------------ | ----------------------------------------------------------------------------- |
| 1.Ảnh 817bca71-00000000.jpg (Vùng sidewalk góc dưới bên phải màn hình, gần rìa ảnh). | Sidewalk hay Road                                    | ranh giới mờ do cát phủ    | Quyết định gán là sidewalk theo hướng tiếp giáp tòa nhà            |
| 2. Ảnh 000000350023.jpg (CCột biển báo gắn liền cột điện).                             | Gán chung`pole` hay tách riêng `traffic sign` | Biển báo gắn trên cột     | Tách riêng phần bảng hiệu là`traffic sign`, thân cột là `pole`   |
| 3. Bụi cây thấp ven đường                                                                 | `vegetation` hay `sidewalk`                      | Lá cây bò tràn ra đường | Gán toàn bộ phần có lá cây là`vegetation` để đảm bảo độ phủ |
