# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Cần quy tắc riêng, không gọi là `DUPLICATE`. Hai camera nhìn cùng một vật ở góc xe nên hai box trên hai ảnh là hai quan sát. `DUPLICATE` chỉ dùng khi hai box cùng một ảnh, cùng một vật. Chưa có timestamp, calibration và policy output thì không xóa box nào.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera. Cùng camera, còn thấy cùng vật thì giữ track ID. Hình đổi mạnh thì thêm keyframe. Vật ra khỏi vòng kính thì Outside, không kéo box vào vành đen. Nối track sang camera kia chỉ khi có timestamp khớp, calibration, và quy tắc seam. Ảnh đơn lẻ không đủ.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Trên `adasind_258420.jpg`, L1 và L2 tôi thấy là người và xe máy ở cụm xa, nhưng so với reference thì là SPURIOUS. Tôi giữ nguyên bản khóa và ghi rework là chưa sửa. Làm lại tôi sẽ không box vật mid chỉ vừa hơn 40 px nếu không thấy rõ đầu hoặc bánh, đúng hướng rule v1.1.0.
