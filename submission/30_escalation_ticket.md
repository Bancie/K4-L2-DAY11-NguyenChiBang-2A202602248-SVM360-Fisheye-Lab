# Escalation ticket

## Ticket 1

- **Frame:** adasind_236370.jpg (cùng kiểu lỗi lặp lại trên adasind_258420.jpg và adasind_310008.jpg)
- **Ảnh chụp:** submission/screenshots/258420-frame.png
- **Expected impact:** Bảng zone mid đang có 14 SPURIOUS. Nếu tính hết vào lỗi người gán nhãn, recall/precision của slice bị đọc sai. Phần lớn là hộp chỉ model có, không phải box L vẽ thừa.
- **Owner:** ai_team
- **Recommendation:** Không sửa nhãn L cho các ca `M_only`. Tách báo cáo model khỏi báo cáo annotator. Soát lại model trên ảnh fisheye và class ThreeWheeler trước khi dùng số mid làm chất lượng người gán nhãn. Finding tương ứng: `adasind_236370.jpg` M2, `action=escalate`.
