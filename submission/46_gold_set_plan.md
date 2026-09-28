# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Vật ở rìa gần seam với left/right | Một xe có thể có box thứ hai trên camera hông | Giữ ảnh fisheye gốc, không chấm trên BEV; giữ nội tham vòng kính | Hai người soát độc lập, chỉ nhận khi cùng class và IoU đủ |
| rear | Xe sát đuôi và phần ego che đáy | Dễ box nhầm thân xe mình thành xe khác | Giữ polygon ego nếu guideline có, và timestamp | Người thứ hai xem ảnh gốc, không xem box của người thứ nhất |
| left | Xe máy sát rìa và góc trước-trái | Méo mạnh, box chữ nhật thừa nền | Giữ calibration camera trái riêng, không dùng số của front | Soát hard slice trước normal; ghi ca không đủ nét là chưa gold |
| right | Seam trước-phải, vật bị vòng kính cắt | truncated dễ bị gán nhầm thành occluded | Giữ cùng bộ rule class với ba camera kia | Không gọi gold nếu hai người lệch class |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): khi thay ống kính, vị trí gắn camera, hoặc khi rule class/ngưỡng kích thước đổi như bản vá v1.1.0. Frame gold cũ không tự còn hiệu lực.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: một xe ở góc trước-trái thấy trên cả front và left. Cần cùng timestamp, calibration hai camera, và quyết định output giữ cả hai box hay một box trên BEV. Không xóa một box chỉ vì thấy hai lần.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: ADASIND và slice B4-edge chỉ là một camera. Hai người đồng ý trên ảnh đó không nói gì về seam, BEV, hay camera rear/left/right. Teaching reference của lab cũng không phải gold set bốn camera.
