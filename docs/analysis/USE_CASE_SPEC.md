# USE CASE SPECIFICATION

## Hệ thống gợi ý thực đơn cá nhân hóa

**Phiên bản:** 1.0 (Draft)  
**Tài liệu tham chiếu:** `docs/SRS.md`, `docs/analysis/BUSINESS_ANALYSIS.md`

## 1. Mục đích

Đặc tả các chức năng của hệ thống theo góc nhìn người sử dụng, làm cơ sở thiết kế UML, Database, API và Test Case.

## 2. Tác nhân

- **User:** Người dùng hệ thống.
- **Admin:** Quản trị viên, quản lý dữ liệu và cấu hình hệ thống.

Các mô-đun M1–M4 là thành phần xử lý nội bộ, không phải tác nhân bên ngoài.

## 3. Đặc tả Use Case

### UC01: Quản lý hồ sơ cá nhân

- **Actor:** User
- **Liên kết:** FR01
- **Tiền điều kiện:** Người dùng đã truy cập hệ thống.
- **Kích hoạt:** Người dùng chọn tạo hoặc chỉnh sửa hồ sơ.

**Luồng chính:**

1. Hệ thống hiển thị biểu mẫu thông tin cá nhân.
2. Người dùng nhập tuổi, giới tính, chiều cao, cân nặng, mức vận động và mục tiêu.
3. Hệ thống kiểm tra tính hợp lệ.
4. Hệ thống lưu thông tin.
5. Hiển thị thông báo thành công.

**Ngoại lệ:** Thông tin thiếu, sai định dạng hoặc nằm ngoài phạm vi hợp lệ.

**Hậu điều kiện:** Hồ sơ được lưu và sẵn sàng cho chức năng tính TDEE.

### UC02: Chọn chế độ ăn và nguyên liệu kiêng

- **Actor:** User
- **Liên kết:** FR02
- **Tiền điều kiện:** Có hồ sơ người dùng hợp lệ.

**Luồng chính:**

1. Hiển thị danh sách 10 chế độ ăn.
2. Người dùng chọn chế độ ăn.
3. Người dùng khai báo nguyên liệu kiêng, dị ứng và ngân sách nếu có.
4. Hệ thống kiểm tra thông tin.
5. Lưu các ràng buộc.

**Ngoại lệ:** Ràng buộc không hợp lệ hoặc mâu thuẫn.

**Hậu điều kiện:** Các ràng buộc được sử dụng khi gợi ý và tối ưu thực đơn.

### UC03: Chọn số bữa ăn

- **Actor:** User
- **Liên kết:** FR03

**Luồng chính:**

1. Hệ thống hiển thị số bữa từ 2 đến 6.
2. Người dùng lựa chọn.
3. Hệ thống lưu số bữa.
4. Cập nhật tỷ lệ phân bổ năng lượng.

**Ngoại lệ:** Số bữa không thuộc khoảng 2–6.

**Hậu điều kiện:** Số bữa được lưu để sử dụng khi lập thực đơn.

### UC04: Tính nhu cầu dinh dưỡng

- **Actor:** User
- **Liên kết:** FR04
- **Tiền điều kiện:** Hồ sơ và mục tiêu hợp lệ.

**Luồng chính:**

1. Người dùng yêu cầu tính năng lượng.
2. Hệ thống lấy dữ liệu hồ sơ.
3. Tính BMR theo công thức Mifflin-St Jeor.
4. Tính TDEE dựa trên mức vận động.
5. Điều chỉnh calories theo mục tiêu.
6. Phân bổ protein, chất béo và carbohydrate.
7. Hiển thị kết quả.

**Ngoại lệ:** Thiếu thông tin cần thiết hoặc không tính được mục tiêu hợp lệ.

**Hậu điều kiện:** Có bộ mục tiêu dinh dưỡng dùng cho lập thực đơn.

### UC05: Gợi ý thực đơn ngày

- **Actor:** User
- **Liên kết:** FR05
- **Tiền điều kiện:** Hồ sơ, mục tiêu và chế độ ăn hợp lệ.

**Luồng chính:**

1. Người dùng chọn tạo thực đơn ngày.
2. Hệ thống lấy hồ sơ và các ràng buộc.
3. Tính mục tiêu năng lượng.
4. M2 xếp hạng món ăn phù hợp.
5. M3 tối ưu lựa chọn món và định lượng nguyên liệu.
6. Hệ thống tạo thực đơn.
7. Hiển thị món ăn, khối lượng và dinh dưỡng.
8. Lưu thực đơn.

**Ngoại lệ:**

- Không có đủ món phù hợp.
- Bộ tối ưu không tìm được nghiệm.
- Dữ liệu dinh dưỡng không đầy đủ.
- Mô hình gợi ý không khả dụng.

**Hậu điều kiện:** Thực đơn hợp lệ được lưu, hoặc lỗi được thông báo rõ ràng.

### UC06: Gợi ý thực đơn tuần

- **Actor:** User
- **Liên kết:** FR06
- **Tiền điều kiện:** Có hồ sơ và mục tiêu dinh dưỡng.

**Luồng chính:**

1. Người dùng chọn tạo thực đơn 7 ngày.
2. Hệ thống xác định mục tiêu mỗi ngày.
3. M2 xếp hạng món phù hợp.
4. M3 tối ưu thực đơn theo ngày và các giới hạn tuần.
5. Kiểm tra quy tắc lặp món.
6. Hiển thị và lưu thực đơn tuần.

**Ngoại lệ:** Không đủ món đa dạng hoặc ràng buộc khiến bài toán vô nghiệm.

**Hậu điều kiện:** Thực đơn tuần đáp ứng các ràng buộc đã thống nhất.

### UC07: Quản lý thực phẩm có sẵn

- **Actor:** User
- **Liên kết:** FR07

**Luồng chính:**

1. Người dùng mở danh sách thực phẩm có sẵn.
2. Thêm nguyên liệu, khối lượng và hạn sử dụng nếu có.
3. Hệ thống kiểm tra dữ liệu.
4. Lưu thông tin.
5. Cập nhật lượng nguyên liệu có thể sử dụng.

**Ngoại lệ:** Nguyên liệu không tồn tại, số lượng âm hoặc dữ liệu không hợp lệ.

**Hậu điều kiện:** Danh sách thực phẩm có sẵn được cập nhật.

### UC08: Tạo danh sách đi chợ

- **Actor:** User
- **Liên kết:** FR08
- **Tiền điều kiện:** Đã có thực đơn.

**Luồng chính:**

1. Người dùng yêu cầu xem danh sách đi chợ.
2. Hệ thống tổng hợp nguyên liệu của các món.
3. Gộp những nguyên liệu trùng nhau.
4. Trừ khối lượng thực phẩm có sẵn còn sử dụng được.
5. Hiển thị lượng nguyên liệu cần mua.

**Ngoại lệ:** Không có thực đơn hoặc dữ liệu nguyên liệu bị thiếu.

**Hậu điều kiện:** Danh sách đi chợ được tạo.

### UC09: Ghi nhật ký ăn uống

- **Actor:** User
- **Liên kết:** FR09

**Luồng chính:**

1. Người dùng nhập câu mô tả món đã ăn.
2. M1 phân tích ý định, món ăn và khẩu phần.
3. Hệ thống tìm món tương ứng.
4. Quy đổi khẩu phần sang gam.
5. Tính lượng dinh dưỡng đã ăn.
6. Lưu nhật ký.
7. Tính lại các bữa chưa ăn nếu cần.

**Ngoại lệ:**

- NLP không hiểu câu nhập.
- Không tìm thấy món.
- Không có dữ liệu quy đổi khẩu phần.
- Người dùng cần xác nhận thông tin được nhận diện.

**Hậu điều kiện:** Nhật ký được lưu với thông tin đã xác nhận.

### UC10: Đổi, giữ hoặc bỏ món

- **Actor:** User
- **Liên kết:** FR10
- **Tiền điều kiện:** Có món được đề xuất.

**Luồng chính:**

1. Người dùng chọn hành động giữ, đổi hoặc bỏ món.
2. Hệ thống ghi nhận hành động.
3. Nếu đổi món, M2 tìm món thay thế.
4. M3 tính lại khẩu phần phù hợp.
5. Cập nhật thực đơn.
6. Hiển thị kết quả.

**Ngoại lệ:** Không tìm được món thay thế phù hợp.

**Hậu điều kiện:** Thực đơn được cập nhật nếu hành động yêu cầu thay đổi.

### UC11: Học từ phản hồi

- **Actor:** User
- **Liên kết:** FR11
- **Tiền điều kiện:** Có phản hồi gắn với một món ăn.

**Luồng chính:**

1. Người dùng thực hiện hành động phản hồi.
2. Hệ thống lưu người dùng, món ăn, hành động và thời điểm.
3. M4 chuyển phản hồi thành tín hiệu học theo cơ chế được thiết kế.
4. Cập nhật thông tin ưu tiên món ăn.
5. Kết quả được sử dụng trong các lần gợi ý tiếp theo.

**Ngoại lệ:** Phản hồi không hợp lệ, mất liên kết người dùng hoặc món ăn, mô-đun học không khả dụng.

**Hậu điều kiện:** Phản hồi được ghi nhận; quá trình cập nhật có thể được thực hiện theo cơ chế đồng bộ hoặc bất đồng bộ đã thống nhất.

## 4. Quan hệ giữa các Use Case

- UC05 và UC06 sử dụng kết quả UC04.
- UC05 và UC06 áp dụng thông tin từ UC02, UC03.
- UC08 phụ thuộc vào thực đơn được tạo.
- UC09 có thể kích hoạt tính toán lại thực đơn.
- UC10 phát sinh từ thực đơn được gợi ý.
- UC11 sử dụng phản hồi được ghi nhận trong UC10.

Các quan hệ nghiệp vụ trên chưa mặc định tương ứng trực tiếp với ký hiệu UML `include` hoặc `extend`. Phải xem xét điều kiện bắt buộc và hành vi tùy chọn khi vẽ sơ đồ.

## 5. Tiêu chí hoàn thành

- Có đầy đủ UC01–UC11.
- Mỗi Use Case có tác nhân và liên kết yêu cầu chức năng.
- Có tiền điều kiện, luồng chính, ngoại lệ và hậu điều kiện.
- Không mâu thuẫn với SRS.
- Các trường hợp ngoại lệ quan trọng có thể chuyển thành Test Case.

**Trạng thái:** Draft, chờ nhóm rà soát và xác nhận.
