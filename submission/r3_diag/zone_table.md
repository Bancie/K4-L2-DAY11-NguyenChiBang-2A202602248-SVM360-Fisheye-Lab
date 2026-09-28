# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 4 | 0 | 0 | 2 | 2 | — |
| mid | 9 | 1 | 3 | 3 | 8 | SPURIOUS (2) |
| edge | 7 | 0 | 0 | 1 | 1 | — |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: cả hai gãy nhiều nhất ở **mid**. L thiếu 1 và thừa 3, lỗi chính là SPURIOUS (2). M thiếu 3 và thừa 8. Center và edge của L đều 0 thiếu / 0 thừa; M ở center thiếu 2 thừa 2, ở edge thiếu 1 thừa 1.
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: gần như mọi lệch của L nằm ở `adasind_258420.jpg`, cụm xe nhỏ phía xa vừa vượt ngưỡng 40 px. M bỏ sót vài vật mà L và R cùng thấy, đồng thời thêm nhiều hộp chỉ mình M có, nhất là mid. Đó là giả thuyết model lệch miền (ảnh phẳng, không quen xe ba bánh và méo fisheye), dựa trên nhiều ca M_only chứ không phải một hộp. `ego_body` không phải nguồn lệch của bảng này. Slice chỉ có ba frame nên không kết luận được cho cả camera.
