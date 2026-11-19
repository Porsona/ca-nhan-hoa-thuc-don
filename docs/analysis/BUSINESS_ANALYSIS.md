# BUSINESS ANALYSIS

## Phân tích nghiệp vụ hệ thống gợi ý thực đơn cá nhân hóa

**Tài liệu tham chiếu:** `docs/SRS.md`

## 1. Mục tiêu nghiệp vụ

Hệ thống hỗ trợ người dùng xây dựng thực đơn món Việt phù hợp với nhu cầu dinh dưỡng, sở thích và các ràng buộc cá nhân.

Các vấn đề cần giải quyết:

- Người dùng không biết nên lựa chọn món ăn nào.
- Khó tính toán lượng dinh dưỡng của từng bữa.
- Thực đơn thông thường chưa xét đến sở thích cá nhân.
- Người dùng gặp khó khăn khi lập thực đơn và danh sách đi chợ.

## 2. Các tác nhân

### ACT-01: Người dùng

- Tạo và cập nhật hồ sơ.
- Chọn mục tiêu dinh dưỡng.
- Khai báo chế độ ăn và món kiêng.
- Yêu cầu gợi ý thực đơn.
- Quản lý thực phẩm có sẵn.
- Đổi món và gửi phản hồi.
- Ghi nhật ký ăn uống.

### ACT-02: Quản trị viên

- Quản lý món ăn và công thức.
- Quản lý nguyên liệu và dữ liệu dinh dưỡng.
- Quản lý các chế độ ăn.
- Kiểm tra dữ liệu và kết quả mô hình.

## 3. Danh sách Use Case

| ID | Tên Use Case | Yêu cầu liên quan |
|---|---|---|
| UC01 | Quản lý hồ sơ cá nhân | FR01 |
| UC02 | Chọn chế độ ăn và món kiêng | FR02 |
| UC03 | Chọn số bữa trong ngày | FR03 |
| UC04 | Tính nhu cầu dinh dưỡng | FR04 |
| UC05 | Gợi ý thực đơn ngày | FR05 |
| UC06 | Gợi ý thực đơn tuần | FR06 |
| UC07 | Quản lý thực phẩm có sẵn | FR07 |
| UC08 | Tạo danh sách đi chợ | FR08 |
| UC09 | Ghi nhật ký ăn uống | FR09 |
| UC10 | Đổi, giữ hoặc bỏ món | FR10 |
| UC11 | Ghi nhận và học từ phản hồi | FR11 |

Các Use Case quản trị sẽ được đặc tả riêng sau khi thống nhất phạm vi quản trị viên.

## 4. Quy trình nghiệp vụ chính

### BP01: Gợi ý thực đơn

1. Người dùng nhập thông tin cá nhân.
2. Chọn mục tiêu và chế độ ăn.
3. Khai báo những nguyên liệu cần tránh.
4. Hệ thống kiểm tra dữ liệu đầu vào.
5. Hệ thống tính TDEE và macro.
6. Mô hình ML xếp hạng các món phù hợp.
7. Bộ tối ưu lựa chọn món và định lượng.
8. Hệ thống trả về thực đơn.
9. Người dùng xem hoặc yêu cầu thay đổi món.

### BP02: Ghi nhật ký

1. Người dùng nhập món đã ăn.
2. NLP phân tích tên món và khẩu phần.
3. Hệ thống tìm món tương ứng và quy đổi khẩu phần.
4. Lưu thông tin nhật ký.
5. Tính năng lượng đã sử dụng.
6. Điều chỉnh các bữa còn lại nếu khả thi.

### BP03: Học sở thích

1. Hệ thống đưa ra món gợi ý.
2. Người dùng giữ, đổi hoặc bỏ món.
3. Hệ thống lưu phản hồi.
4. Mô-đun học từ phản hồi cập nhật mức ưu tiên.
5. Phản hồi được sử dụng trong các lần gợi ý tiếp theo.

## 5. Quy tắc nghiệp vụ

- BR01: Mỗi thực đơn phải tuân thủ chế độ ăn và nguyên liệu bị cấm.
- BR02: Số bữa mỗi ngày nằm trong khoảng 2–6.
- BR03: Thực đơn ngày phải hướng tới mục tiêu dinh dưỡng đã tính.
- BR04: Một món không được lặp quá 2 lần trong thực đơn tuần theo yêu cầu đề cương.
- BR05: Khi không tìm được thực đơn khả thi, hệ thống phải thông báo và không được tự ý bỏ qua ràng buộc dị ứng.
- BR06: Phản hồi người dùng phải được ghi nhận trước khi sử dụng để cập nhật sở thích.

## 6. Các tình huống ngoại lệ cần phân tích

- Người dùng thiếu thông tin.
- Không tìm thấy món ăn.
- Không đủ dữ liệu công thức.
- Món ăn không phù hợp chế độ ăn.
- Bài toán tối ưu không có nghiệm.
- NLP không hiểu câu nhập.
- Người dùng mới chưa có lịch sử đánh giá.
- Mô hình ML không khả dụng.

## 7. Tiêu chí hoàn thành tài liệu

- Xác định được các tác nhân.
- Có danh sách Use Case liên kết với SRS.
- Mô tả được các luồng nghiệp vụ chính.
- Liệt kê các quy tắc nghiệp vụ và ngoại lệ.
- Được nhóm rà soát trước khi thiết kế chi tiết.

**Trạng thái:** Bản nháp cần nhóm thống nhất.
