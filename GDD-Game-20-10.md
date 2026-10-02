# Game Design Document — Cửa hàng hoa 20/10

> **Trạng thái:** Bản đề xuất để cùng duyệt ý tưởng  
> **Tên công ty:** [Để trống]  
> **Phiên bản:** 0.1  
> **Ngày:** 02/10/2026

## 1. Tóm tắt

Mini game sân khấu tương tác cho sự kiện 20/10. Năm đội, mỗi đội ba người, cùng vận hành một cửa hàng hoa qua bốn thử thách ngắn: chăm vườn, bê chậu, chở cây và sáng tạo tên cửa hàng. Người chơi điều khiển bằng điện thoại cá nhân sau khi quét QR; khán giả theo dõi màn hình lớn và có thể thả emoji cổ vũ.

**Trải nghiệm cốt lõi:** Mỗi thành viên nắm một phần điều khiển hoặc thông tin. Đội phải giao tiếp và phối hợp mới vượt qua thử thách.

**Mục tiêu sự kiện:** Vui vẻ, nhịp nhanh, ai cũng có lượt chơi và chương trình không kéo dài.

## 2. Bối cảnh và quy mô

- **Đối tượng:** 15 chị em trong công ty.
- **Đội hình:** 5 đội × 3 người.
- **Hình thức:** Tổ chức trực tiếp, kết hợp giao diện web trên điện thoại và màn hình lớn của quản trò.
- **Thời lượng game:** Khoảng 20–30 phút; cần kiểm tra bằng chạy thử với đủ lượt cho cả 5 đội.
- **Thời gian phát triển:** 2 tuần, 2 nhân sự phát triển có hỗ trợ AI Agent.
- **Thiết bị:** Điện thoại cá nhân; có điện thoại dự phòng khi trục trặc. Chi phí và lựa chọn hạ tầng để mở.
- **Tên công ty:** Để trống, có thể bổ sung sau.

## 3. Phong cách và chủ đề

- **Chủ đề:** Cửa hàng hoa vui nhộn, thi đua thân thiện.
- **Hình ảnh:** Màu tươi sáng, pastel, hơi cute và có chút cảm giác công chúa; giữ tương phản rõ khi chiếu màn hình lớn.
- **Bảng màu gợi ý:** Hồng phấn, tím lavender, vàng kem, xanh mint; màu điểm số và trạng thái phải dễ phân biệt.
- **Giọng điệu:** Hóm hỉnh, tích cực, cổ vũ hợp tác; tránh làm người chơi thấy xấu hổ.
- **Đạo cụ hình ảnh:** Chậu hoa, bình tưới, kéo tỉa, sâu hoạt hình, xe giao hàng, bảng hiệu và hiệu ứng lấp lánh vừa phải.

## 4. Cấu trúc và vận hành

### Luồng dự kiến

1. Quản trò giới thiệu luật, hiển thị QR vào sảnh.
2. Người chơi quét QR, tự nhập tên, vào sảnh và ghép đội ba người theo hướng dẫn của quản trò.
3. Quản trò xác nhận đội hình và lần lượt bắt đầu các vòng.
4. Mỗi vòng, các đội chơi cùng một thử thách theo lượt. Đội đang chờ xem màn hình và thả emoji cổ vũ.
5. Hệ thống lưu kết quả từng lượt, cập nhật bảng điểm tổng.
6. Kết thúc bốn vòng, hiển thị thứ hạng và trao thưởng theo tổng điểm.

### Điều khiển của quản trò

Màn hình quản trò là màn hình chính. Quản trò có thể bắt đầu lượt, kết thúc lượt thủ công, tính lại/reset lượt, theo dõi đội đang chơi, thời gian và điểm, cũng như chuyển giữa hướng dẫn, sân chơi, kết quả vòng và bảng tổng. Thao tác reset nên yêu cầu xác nhận để tránh mất kết quả do bấm nhầm.

### Ghép đội và thứ tự vòng

- Không cần tên đội; màn hình có thể dùng tên người chơi hoặc nhãn “Đội 1–5”.
- Có đề xuất đưa thử thách làm bảng hiệu lên trước để tạo đội/khởi động, nhưng thứ tự chưa chốt. Vì việc ghép đội có thể thực hiện tại sảnh trước khi chơi, vòng này hiện không bắt buộc để tạo đội.
- Thứ tự vòng trong tài liệu là thứ tự thiết kế hiện tại, có thể đổi sau playtest.

## 5. Các vòng chơi

### Vòng 1 — Trồng cây

**Mục tiêu:** Chăm sóc đúng cây trong khu vườn trong thời gian giới hạn để tích lũy điểm.

Mỗi đội có vườn riêng dạng lưới `m × n`. Cây và trạng thái chăm sóc hiển thị công khai trên màn hình lớn. Người chơi nhìn màn hình chung, phối hợp điều khiển qua điện thoại:

- Người A điều khiển con trỏ lên/xuống.
- Người B điều khiển con trỏ trái/phải.
- Người C chọn dụng cụ: tưới nước, bắt sâu hoặc cắt tỉa.

Khi quản trò bắt đầu lượt, đồng hồ chạy. Đội đưa con trỏ đến cây, chọn dụng cụ đúng và xác nhận thao tác. Mỗi lần chăm sóc đúng được `X` điểm. Hết giờ thì khóa điều khiển và chốt điểm.

**Cần cân chỉnh:** Cỡ lưới, số cây, thời lượng, điểm `X`, cách xác nhận, cây có cần nhiều hành động hay không; thao tác sai có mất thời gian hoặc bị trừ điểm không.

### Vòng 2 — Bê cây

**Mục tiêu:** Ba người cùng đưa chậu cây tới điểm tập kết.

Cả ba cùng điều khiển một chậu. Chậu di chuyển khi người chơi ở đủ gần nhau; nếu tách quá xa thì chậu rơi. Có chướng ngại vật trên đường. Khi rơi, đội phải dừng để “hốt đất”, chịu phạt thời gian rồi mới đi tiếp.

Ghi thời gian hoàn thành và đổi thứ tự thành điểm vòng. Quá mốc tối đa thì không có điểm. Mốc thua dự kiến khoảng 2–3 phút, cần cân bằng qua chơi thử.

**Cần cân chỉnh:** Ngưỡng khoảng cách, tốc độ, chướng ngại vật, thời gian phạt, vị trí tiếp tục sau khi rơi, mốc tối đa chính xác và bảng đổi thứ hạng sang điểm.

### Vòng 3 — Chở cây

**Mục tiêu:** Lái xe chở cây tới cửa hàng, tránh chướng ngại vật.

- Người A điều khiển sang trái.
- Người B điều khiển sang phải.
- Người C giữ để tăng tốc; thả ra thì xe tự giảm tốc.

Ghi thời gian hoàn thành và đổi thứ tự thành điểm vòng. Quá mốc tối đa thì không có điểm; mốc dự kiến khoảng 2–3 phút và cần playtest.

**Cần cân chỉnh:** Thao tác trái/phải là giữ để lái hay bấm theo nhịp; cách xử lý va chạm; độ khó đường; tốc độ tăng/giảm; mốc tối đa và quy đổi điểm.

### Vòng 4 — Làm biển hiệu

**Mục tiêu:** Đội phối hợp vẽ và đoán để tạo tên cửa hàng hài hước.

Mỗi đội chọn từ khóa trong ba lượt, ghép thành tên theo mẫu:

> **Tên hoa + Tính từ + Danh từ**

Tên hoa dễ nhất, danh từ khó hơn, tính từ khó nhất. Có thể tạo tên vô lý hoặc hài hước.

Trong một lượt, hai người thấy từ khóa và cùng vẽ trên thiết bị; người thứ ba chỉ thấy số ký tự và là người đoán. Mỗi tranh chia thành 16 ô như bàn cờ. Hai tranh đan xen; một người lấy ô đen, người kia lấy ô trắng. Người đoán nhìn ảnh ghép và độ dài từ để đoán.

Thời gian vẽ thay đổi theo độ khó, dự kiến 60/75/90 giây. Người đoán có số lần đoán giới hạn và được thưởng nếu đoán đúng khi còn lượt.

**Cần làm rõ:** Hai người vẽ tranh riêng rồi nộp trước khi ghép; thứ tự và cách chọn ô đen/trắng; số lần đoán ban đầu; điểm thưởng theo lượt đoán còn lại; điểm cho từng từ. Các con số để mở tới playtest.

## 6. Điểm số và chiến thắng

- Tổng điểm cuối bằng điểm của bốn vòng; xếp hạng theo tổng và trao thưởng theo thứ hạng.
- Vòng 1: điểm theo số lần chăm sóc đúng.
- Vòng 2–3: ghi thời gian hoàn thành rồi quy thứ tự thành điểm để chuẩn hóa giữa trò chơi.
- Vòng 4: điểm theo số từ đoán đúng, có thưởng nếu đoán đúng khi còn lượt.
- Bảng điểm hiển thị điểm từng vòng và tổng điểm.

**Cần quyết định:** Thang điểm mỗi vòng, trọng số, luật hòa điểm và có điểm tham gia cho đội không hoàn thành trong mốc tối đa hay không (hiện dự kiến 0 điểm ở vòng 2–3).

## 7. Nhịp độ

Mỗi đội chơi độc lập theo lượt trong từng vòng; thời lượng mỗi lượt thay đổi theo trò và cần ngắn để đội chờ không sốt ruột. Có 5 đội × 4 vòng = 20 lượt đội. Để giữ game trong 20–30 phút, trung bình mỗi lượt cộng chuyển đội cần khoảng 60–90 giây. Mốc tối đa 2–3 phút ở vòng 2–3 có thể khiến chương trình vượt thời lượng; cần chạy thử toàn bộ luồng 5 đội, gồm giới thiệu, chuyển lượt, reset, bảng điểm và trao thưởng.

## 8. Giao diện

### Điện thoại người chơi

Giao diện tối giản, ưu tiên nút điều khiển lớn và trạng thái dễ hiểu. Tùy vòng, hiển thị tên người chơi/nhóm, nút điều khiển, trạng thái kết nối, đồng hồ hoặc lượt đoán cần thiết. Người đoán chỉ thấy thông tin được phép: ảnh ghép và số ký tự, không thấy từ khóa.

### Màn hình quản trò và khán giả

Hiển thị QR/hướng dẫn vào sảnh, danh sách người chơi và trạng thái ghép đội, sân chơi, đội đang chơi, thời gian, mục tiêu, kết quả từng lượt/vòng, bảng tổng và emoji cổ vũ. Emoji cần được bố trí để không che nội dung thi đấu.

## 9. Yêu cầu trải nghiệm và vận hành

- Hướng dẫn mỗi vòng ngắn, có minh họa vai trò.
- Cả ba thành viên đều có thao tác có ý nghĩa.
- Khán giả dễ hiểu diễn biến và thứ hạng.
- Giao diện đọc rõ trên điện thoại và màn chiếu.
- Hình phạt được thể hiện vui vẻ, không làm người chơi xấu hổ.
- Quản trò có thể khôi phục lượt; có điện thoại dự phòng.
- Kiểm tra mạng tại địa điểm, quét QR và phản hồi đồng thời trước sự kiện.

## 10. Phạm vi phát triển đề xuất

**Bản cần có:** Sảnh QR, nhập tên, ghép nhóm ba người theo hướng dẫn quản trò; bốn mini game; màn hình quản trò để bắt đầu/kết thúc/reset; đồng hồ, điểm và bảng tổng; màn hình trình chiếu; emoji cổ vũ đơn giản; cách cho người chơi tham gia lại hoặc quản trò gán lại phiên khi đổi sang điện thoại dự phòng.

**Để mở:** Nền tảng và hạ tầng, trình duyệt hỗ trợ, chi phí hosting/dịch vụ, âm thanh/nhạc/hiệu ứng nâng cao, tùy biến logo công ty, chống gian lận, dữ liệu lưu trữ và thời gian lưu.

## 11. Playtest và tiêu chí thành công

Cần thử và cân bằng thời lượng, điểm, độ khó, điều khiển, phạt, từ khóa, số lần đoán, quy đổi thứ hạng, độ trễ và khả năng đọc màn hình.

**Tiêu chí đạt:** Người chơi hiểu vai trò nhanh; cả ba phải phối hợp; khán giả hiểu diễn biến; lượt không kéo dài; ai cũng có cơ hội chơi; không khí vui và có tiếng cười.

## 12. Câu hỏi còn mở trước khi bàn giao phát triển

1. Chốt thứ tự bốn vòng; vòng làm biển hiệu có nên mở đầu không?
2. Mục tiêu thời lượng chính xác của mỗi lượt để giữ tổng game 20–30 phút?
3. Vòng 1 có bao nhiêu cây, lưới cỡ nào, thao tác sai bị xử lý ra sao?
4. Vòng 2–3 dùng mốc tối đa chính xác nào trong khoảng 2–3 phút?
5. Chậu rơi bị phạt bao nhiêu giây và tiếp tục từ đâu?
6. Vòng 4: mỗi đội có tổng cộng ba từ, mỗi từ một lượt, đúng không? Hai tranh ghép xen kẽ tạo một ảnh cho lượt đoán đó?
7. Mỗi lượt vòng 4, hai người cùng vẽ một từ hay mỗi người vẽ phiên bản riêng của cùng từ?
8. Có bao nhiêu lần đoán và thưởng thế nào theo số lượt còn lại?
9. Thang điểm, trọng số và luật hòa điểm?
10. Quản trò gán người vào nhóm bằng thao tác nào?

## 13. Pitch ngắn

Trong một cửa hàng hoa vừa ngọt ngào vừa hỗn loạn, ba người bạn chia nhau điều khiển để chăm vườn, bê chậu, lái xe giao cây và nghĩ tên tiệm. Mỗi người chỉ có một phần thông tin hoặc quyền điều khiển; muốn thắng thì phải phối hợp ăn ý. Khán giả cổ vũ qua màn hình lớn và cùng chờ xem đội nào mở được cửa hàng hoa có cái tên khó đỡ nhất.
