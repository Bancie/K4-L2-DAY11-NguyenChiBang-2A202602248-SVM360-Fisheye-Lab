# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| adasind_258420.jpg, zone mid | L1 và L2 SPURIOUS; L8/R5 lệch hình Car | Hầu hết lỗi của người nằm ở frame này, vật vừa vượt 40 px | annotations.xml đã khóa, submission/screenshots/258420-pedestrian.png, findings L1 L2 |
| adasind_258420.jpg và adasind_310008.jpg, hộp M_only | Nhiều SPURIOUS chỉ model có ở mid | Nếu không tách model, bảng mid bị đọc thành lỗi annotator | model_compare.md, finding M2 action=escalate, 30_escalation_ticket.md |

Giới hạn của kết luận từ ba frame ADASIND: chỉ một camera fisheye, ba frame, gần như mọi lệch của L nằm ở một frame. Không suy ra tỷ lệ lỗi của front/rear/left/right hay của 50.000 frame.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: chọn frame cách nhau theo thời gian và theo camera, không lấy một đoạn video liên tiếp rồi đếm 200 lần. Mỗi camera có ô normal và hard. Hai trăm frame này là hàng đợi review, chưa phải mẫu ngẫu nhiên đủ để ước lượng tỷ lệ lỗi của 50.000 frame.
