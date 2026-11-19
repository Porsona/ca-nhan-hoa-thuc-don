
# Activity Diagram

## UC05: Gợi ý thực đơn ngày

### 1. Sơ đồ hoạt động

![Activity Diagram](diagrams/activity-meal-plan.svg)

### 2. Mô tả quy trình

Sơ đồ mô tả quá trình hệ thống tạo thực đơn
cá nhân hóa cho người dùng.

Quy trình gồm:

1. Người dùng nhập hồ sơ và mục tiêu ăn uống.
2. Hệ thống kiểm tra thông tin đầu vào.
3. Tính BMR, TDEE và nhu cầu dinh dưỡng.
4. Lọc các món không phù hợp.
5. Mô hình M2 xếp hạng món ăn.
6. Mô hình M3 tối ưu khẩu phần.
7. Hệ thống lưu và hiển thị thực đơn.

### 3. Các trường hợp ngoại lệ

- Thông tin người dùng không hợp lệ.
- Không tìm được món ăn phù hợp.
- Bộ tối ưu không tìm được nghiệm.

### 4. Tài liệu liên quan

- [SRS](../SRS.md)
- [Use Case Specification](USE_CASE_SPEC.md)
