# QA review · B4-edge

Mã khóa: 5D57-AEBD

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_258420.jpg | L1 | R01 | Hộp `Pedestrian` cao khoảng 51 px ở cụm xe phía xa, bên trái đường. Vật nhỏ, mờ, sát ngưỡng 40 px; cần nhìn lại có đủ người để giữ box hay không. |
| adasind_258420.jpg | L2 | R03 | Hộp `Bike` cao khoảng 52 px cùng cụm xa, đang bật `occluded`. Người và xe hai bánh dính nhau trên ảnh; nếu là người đang lái thì chỉ một hộp `Bike`, không tách thêm người. |
| adasind_258420.jpg | L8 | R02 | Hộp `Car` cao khoảng 44 px, `truncated` đang tắt. Hộp chưa bám sát phần xe nhìn thấy ở phía sau cụm giữa đường. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
