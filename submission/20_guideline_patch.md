# Guideline patch

- **Rule mới đề xuất:** Ở zone `mid`, vật cao từ 40 px đến dưới 60 px chỉ được box khi nhìn rõ từng đối tượng (đầu, bánh, hoặc thân xe). Nếu chỉ là vệt mờ trong cụm xa, không box; ghi vào observations thay vì đoán class.
- **Áp dụng cho:** box của Pedestrian, Bike và Car ở zone mid trên ảnh fisheye một camera. Không đổi `ignore_region` hay ngưỡng của zone center.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R01 bắt mọi vật cao ≥ 40 px phải có box. Trên `adasind_258420.jpg`, L1 cao khoảng 51 px và L2 khoảng 52 px vừa vượt ngưỡng nhưng không đủ nét để tách người với xe. Luật không nói phải làm gì khi vật chỉ "đủ số pixel".
- **`rules_version` mới:** v1.0.0 → v1.1.0
- **Hiệu lực từ:** round r3_diag trở đi, sau khi guideline owner chấp nhận. Không áp hồi tố lên bản đã khóa r1_craft.
