# SOFTWARE REQUIREMENTS SPECIFICATION (SRS)

## HỆ THỐNG GỢI Ý THỰC ĐƠN CÁ NHÂN HÓA DỰA TRÊN HỌC MÁY VÀ TỐI ƯU HÓA DINH DƯỠNG

**Tên tiếng Anh:** Personalized Vietnamese Meal Recommendation System

**Phiên bản:** 1.0 (Draft)

**Môn học:** Học máy nâng cao

**Đơn vị:** Khoa Công nghệ Thông tin, Trường Đại học Xây dựng Hà Nội

**Repository:** `ca-nhan-hoa-thuc-don`

**Trạng thái:** Đang phân tích và thiết kế, chưa nghiệm thu yêu cầu

---

# 1. GIỚI THIỆU

## 1.1. Mục đích tài liệu

Tài liệu SRS mô tả các yêu cầu chức năng, phi chức năng, dữ liệu, giao diện và các ràng buộc kỹ thuật của hệ thống gợi ý thực đơn cá nhân hóa.

SRS được sử dụng làm cơ sở để:

- Phân tích nghiệp vụ và thiết kế UML.
- Thiết kế cơ sở dữ liệu.
- Xây dựng các mô-đun học máy.
- Phát triển Backend và Frontend.
- Xây dựng Test Case.
- Nghiệm thu và đánh giá hệ thống.

## 1.2. Mục tiêu dự án

Phát triển một ứng dụng web giúp người dùng lựa chọn món ăn Việt Nam theo sở thích cá nhân, chế độ ăn và mục tiêu dinh dưỡng.

Hệ thống kết hợp Machine Learning, NLP và tối ưu hóa có ràng buộc.

Nguyên tắc cốt lõi:

**Học máy đề xuất người dùng nên ăn món gì. Bộ tối ưu xác định lượng nguyên liệu phù hợp cho từng món.**

## 1.3. Phạm vi hệ thống

Trong phạm vi:

- Người trưởng thành khỏe mạnh.
- Khoảng 100 món ăn Việt Nam.
- 10 chế độ ăn theo đề cương.
- Thực đơn ngày và tuần.
- Từ 2 đến 6 bữa mỗi ngày.
- Gợi ý món ăn cá nhân hóa.
- Tính BMR, TDEE và các chỉ số dinh dưỡng.
- Tối ưu khẩu phần theo nguyên liệu.
- Quản lý thực phẩm có sẵn.
- Tạo danh sách đi chợ.
- Ghi nhật ký ăn uống bằng tiếng Việt.
- Học sở thích từ phản hồi người dùng.

Ngoài phạm vi:

- Nhận diện món ăn bằng hình ảnh.
- Nhập yêu cầu bằng giọng nói.
- Ứng dụng di động native.
- Tư vấn dinh dưỡng điều trị bệnh lý.
- Phục vụ trẻ em, phụ nữ mang thai và người có nhu cầu dinh dưỡng y khoa đặc biệt.

## 1.4. Thuật ngữ

| Thuật ngữ | Giải thích |
|---|---|
| SRS | Software Requirements Specification |
| BMR | Năng lượng chuyển hóa cơ bản |
| TDEE | Tổng năng lượng tiêu hao hằng ngày |
| Macro | Protein, chất béo, carbohydrate |
| NLP | Xử lý ngôn ngữ tự nhiên |
| Recommendation System | Hệ thống gợi ý |
| Collaborative Filtering | Gợi ý dựa trên tương tác người dùng |
| Content-Based Filtering | Gợi ý dựa trên đặc điểm món ăn |
| MILP | Quy hoạch tuyến tính nguyên hỗn hợp |
| Cold Start | Thiếu dữ liệu về người dùng hoặc món mới |

---

# 2. MÔ TẢ TỔNG QUAN HỆ THỐNG

## 2.1. Đối tượng sử dụng

### Người dùng (User)

Có thể:

- Cung cấp hồ sơ cá nhân.
- Chọn mục tiêu và chế độ ăn.
- Khai báo dị ứng, nguyên liệu cần tránh.
- Nhận thực đơn được gợi ý.
- Đổi hoặc bỏ món.
- Ghi nhật ký ăn uống.
- Đánh giá và phản hồi món ăn.

### Quản trị viên (Admin)

Có thể:

- Quản lý danh mục nguyên liệu.
- Quản lý món ăn và công thức.
- Quản lý chế độ ăn.
- Kiểm tra chất lượng dữ liệu.
- Quản lý mô hình và xem kết quả đánh giá.

Các chức năng quản trị là yêu cầu thiết kế từ tài liệu hệ thống cũ; giao diện quản trị đầy đủ cần được xác nhận trong phạm vi MVP.

## 2.2. Quy trình nghiệp vụ chính

1. Người dùng nhập thông tin cá nhân.
2. Người dùng chọn mục tiêu, chế độ ăn và những nguyên liệu cần tránh.
3. Hệ thống xác định nhu cầu năng lượng.
4. Hệ thống phân tích yêu cầu bằng NLP nếu người dùng nhập câu tự nhiên.
5. Mô hình gợi ý xếp hạng các món phù hợp.
6. Bộ tối ưu tính khẩu phần theo mục tiêu dinh dưỡng.
7. Hệ thống hiển thị thực đơn theo ngày hoặc tuần.
8. Người dùng có thể đổi món, ghi nhật ký và phản hồi.
9. Hệ thống ghi nhận phản hồi để cải thiện các lần gợi ý tiếp theo.

## 2.3. Kiến trúc logic

Hệ thống dự kiến gồm:

- Frontend: Streamlit.
- Backend: FastAPI.
- Database: SQLite.
- NLP Service: M1.
- Recommendation Service: M2.
- Nutrition Optimization Service: M3.
- Feedback Learning Service: M4.

Tất cả các thành phần giao tiếp qua các giao diện dữ liệu được thống nhất trước khi triển khai.

---

# 3. YÊU CẦU CHỨC NĂNG

## FR01. Quản lý hồ sơ người dùng

**Mô tả:** Người dùng nhập và cập nhật thông tin cơ bản.

Đầu vào:

- Tuổi hoặc ngày sinh.
- Giới tính dùng cho công thức BMR.
- Cân nặng (kg).
- Chiều cao (cm).
- Mức vận động.
- Mục tiêu: giảm cân, giữ cân hoặc tăng cân.

Đầu ra: Hồ sơ hợp lệ được lưu trong hệ thống.

Điều kiện nghiệm thu:

- Hệ thống nhận các thông tin hợp lệ.
- Thông báo khi dữ liệu không hợp lệ hoặc thiếu.
- Có thể sử dụng hồ sơ để tính nhu cầu năng lượng.

## FR02. Lựa chọn chế độ ăn và ràng buộc

**Mô tả:** Người dùng cấu hình nhu cầu ăn uống.

Hỗ trợ 10 chế độ ăn:

1. Cân bằng.
2. Ăn chay.
3. Thuần chay.
4. Chay có cá.
5. Linh hoạt.
6. Ít tinh bột.
7. Keto.
8. Địa Trung Hải.
9. Paleo.
10. Thực phẩm nguyên chất.

Người dùng có thể khai báo nguyên liệu không ăn được, nguyên liệu dị ứng và ngân sách.

Điều kiện nghiệm thu:

- Hệ thống lưu chế độ ăn đã chọn.
- Không đưa nguyên liệu bị cấm vào thực đơn.
- Thông báo khi các ràng buộc không thể đồng thời đáp ứng.

## FR03. Lựa chọn số bữa

Người dùng được chọn từ 2–6 bữa mỗi ngày.

Hệ thống phân bổ năng lượng mục tiêu theo quy tắc của từng số bữa đã được định nghĩa.

Điều kiện nghiệm thu:

- Chỉ chấp nhận 2–6 bữa.
- Tổng năng lượng phân bổ bằng năng lượng mục tiêu của ngày, trong giới hạn sai số làm tròn.

## FR04. Tính nhu cầu năng lượng

Hệ thống sử dụng công thức Mifflin-St Jeor để tính BMR.

TDEE được xác định từ BMR và hệ số vận động.

Hệ thống tính:

- BMR.
- TDEE.
- Calories mục tiêu.
- Protein.
- Chất béo.
- Carbohydrate.
- Năng lượng mục tiêu cho từng bữa.

Các mức điều chỉnh mặc định theo đề cương:

- Giảm cân: TDEE − 400 kcal.
- Giữ cân: TDEE.
- Tăng cân: TDEE + 300 kcal.

Điều kiện nghiệm thu:

- Tính đúng theo công thức đã cấu hình.
- Tổng năng lượng từ macro phù hợp mục tiêu sau quy đổi và làm tròn.
- Từ chối dữ liệu đầu vào không hợp lệ.

Lưu ý: Các ngưỡng năng lượng và quy tắc chế độ ăn là tham số của dự án, không thay thế hướng dẫn y khoa cá nhân.

## FR05. Gợi ý thực đơn theo ngày

Hệ thống đề xuất thực đơn cho một ngày dựa trên:

- Hồ sơ và mục tiêu người dùng.
- Chế độ ăn.
- Sở thích.
- Nguyên liệu cần tránh.
- Điểm phù hợp từ mô hình ML.
- Dữ liệu món ăn và dinh dưỡng.

Đầu ra:

- Danh sách bữa ăn.
- Món ăn của từng bữa.
- Định lượng nguyên liệu (gam).
- Tổng calories và macro.

Điều kiện nghiệm thu:

- Món ăn đáp ứng các ràng buộc bắt buộc.
- Mỗi món có thể truy xuất về dữ liệu dinh dưỡng hoặc công thức tương ứng.
- Hệ thống giải thích hoặc thông báo khi không tìm được thực đơn khả thi.

## FR06. Gợi ý thực đơn theo tuần

Hệ thống tạo thực đơn trong 7 ngày.

Yêu cầu:

- Đáp ứng mục tiêu từng ngày.
- Hạn chế lặp món.
- Áp dụng giới hạn theo tuần của chế độ ăn.
- Không lặp một món quá 2 lần/tuần theo quy tắc trong đề cương.

Điều kiện nghiệm thu:

- Hiển thị đầy đủ 7 ngày.
- Áp dụng đúng quy tắc giới hạn món và nguyên liệu.
- Thông báo nếu không thể đáp ứng toàn bộ ràng buộc.

## FR07. Quản lý thực phẩm có sẵn

Người dùng khai báo:

- Nguyên liệu.
- Số lượng tính theo gam.
- Hạn sử dụng nếu có.

Hệ thống ưu tiên dùng nguyên liệu đang có trong quá trình lập thực đơn.

## FR08. Tạo danh sách đi chợ

Hệ thống tổng hợp lượng nguyên liệu cần dùng theo thực đơn.

Lượng cần mua được xác định bằng lượng cần sử dụng trừ lượng còn sẵn có đủ điều kiện sử dụng.

Điều kiện nghiệm thu:

- Gộp đúng các nguyên liệu trùng nhau.
- Không trả về lượng cần mua âm.
- Không tính nguyên liệu hết hạn vào lượng có sẵn.

## FR09. Ghi nhật ký ăn uống

Người dùng nhập câu tiếng Việt, ví dụ:

"Sáng nay tôi ăn một bát phở bò."

Hệ thống phân tích:

- Ý định.
- Tên món.
- Bữa ăn.
- Số lượng.
- Đơn vị khẩu phần.

Hệ thống quy đổi khẩu phần ra gam khi có dữ liệu quy đổi phù hợp, lưu nhật ký và tính lại phần dinh dưỡng còn lại trong ngày.

Nếu không nhận diện được món hoặc khẩu phần, hệ thống yêu cầu người dùng lựa chọn hoặc xác nhận.

## FR10. Đổi, giữ hoặc bỏ món

Người dùng có thể:

- Giữ món được đề xuất.
- Yêu cầu thay món.
- Bỏ món.

Hệ thống tìm món thay thế đáp ứng những ràng buộc bắt buộc và tính toán lại khẩu phần nếu cần.

## FR11. Học sở thích từ phản hồi

Hệ thống ghi nhận hành vi của người dùng đối với món được gợi ý.

Dữ liệu phản hồi được dùng để cập nhật điểm ưu tiên hoặc mô hình học từ phản hồi.

Điều kiện nghiệm thu:

- Mỗi phản hồi có thể liên kết với người dùng và món ăn.
- Ghi nhận thời điểm và loại hành động.
- Cơ chế cập nhật có thể kiểm thử trên dữ liệu mô phỏng.

---

# 4. YÊU CẦU PHI CHỨC NĂNG

| ID | Yêu cầu | Tiêu chí mục tiêu |
|---|---|---|
| NFR01 | Hiệu năng | Lập thực đơn ngày dưới 2 giây trên môi trường CPU được xác định |
| NFR02 | Độ chính xác dinh dưỡng | Calories lệch không quá ±5%; mỗi macro không quá ±10% |
| NFR03 | Tính nhất quán | Không vi phạm nguyên liệu dị ứng đã khai báo |
| NFR04 | Khả năng sử dụng | Giao diện tiếng Việt, biểu mẫu dễ thao tác |
| NFR05 | Bảo mật | Bảo vệ hồ sơ người dùng, hạn chế quyền truy cập dữ liệu |
| NFR06 | Khả năng bảo trì | Chia mô-đun rõ ràng, dễ kiểm thử và thay thế mô hình |
| NFR07 | Khả năng tái lập | Lưu cấu hình và kết quả thực nghiệm ML |
| NFR08 | Độ tin cậy | Báo lỗi rõ ràng khi API hoặc mô hình không khả dụng |

Các ngưỡng NFR01 và NFR02 là mục tiêu thiết kế, không phải kết quả thực nghiệm đã xác nhận.

Các biện pháp bảo mật, cơ chế xác thực và thời gian phản hồi cụ thể cần được hoàn thiện trong thiết kế kỹ thuật.

---

# 5. YÊU CẦU DỮ LIỆU

## 5.1. Dữ liệu nguyên liệu

Nguồn dự kiến:

- Viện Dinh dưỡng Việt Nam.
- USDA FoodData Central.

Thông tin tối thiểu:

- Mã nguyên liệu.
- Tên.
- Nhóm.
- Calories.
- Protein.
- Chất béo.
- Carbohydrate.
- Nguồn dữ liệu.

Giá trị dinh dưỡng được chuẩn hóa theo 100 g phần ăn được.

## 5.2. Dữ liệu món ăn

Hệ thống cần quản lý:

- Mã món.
- Tên món.
- Loại món.
- Bữa ăn phù hợp.
- Danh sách nguyên liệu.
- Khối lượng mặc định.
- Khối lượng tối thiểu và tối đa.
- Thông tin dinh dưỡng.

Danh mục ban đầu hướng tới khoảng 100 món Việt Nam.

## 5.3. Dữ liệu tương tác

Đối với mô hình gợi ý, dữ liệu dự kiến gồm:

- User ID.
- Recipe ID.
- Rating hoặc tín hiệu tương tác.
- Thời gian tương tác.

Food.com được sử dụng để nghiên cứu và đánh giá nhánh Collaborative Filtering.

Đối với món Việt chưa có lịch sử tương tác, hệ thống sử dụng đặc trưng món ăn và phản hồi tích lũy để hỗ trợ cá nhân hóa.

Không coi kết quả trên Food.com là bằng chứng mô hình đã gợi ý tốt món Việt.

## 5.4. Dữ liệu NLP

Các câu yêu cầu ăn uống tiếng Việt được gán nhãn ý định và thực thể.

Các nhóm thực thể gồm:

- Món ăn.
- Bữa ăn.
- Số lượng.
- Đơn vị.
- Mục tiêu.
- Chế độ ăn.
- Nguyên liệu kiêng.
- Thông tin hồ sơ.
- Ngân sách.

Dữ liệu huấn luyện, validation và test phải được phân chia hợp lý và kiểm tra trùng lặp.

---

# 6. YÊU CẦU MACHINE LEARNING

## M1. NLP

**Mục tiêu:** Hiểu câu yêu cầu ăn uống tiếng Việt.

Giải pháp dự kiến:

- Baseline từ điển và regex.
- PhoBERT fine-tuning.

Đầu vào: Câu tiếng Việt.

Đầu ra: Ý định và các thực thể được trích xuất.

Chỉ số: Precision, Recall, F1.

## M2. Recommendation System

**Mục tiêu:** Xếp hạng món ăn theo mức độ phù hợp.

Phương pháp:

- Popularity Baseline.
- Content-Based Filtering.
- Matrix Factorization.
- Hybrid Recommendation.

Đầu vào: Hồ sơ, đặc trưng món và lịch sử tương tác khi có.

Đầu ra: Điểm phù hợp của từng món.

Chỉ số: Recall@10, NDCG@10 trên tập kiểm thử có dữ liệu tương tác.

## M3. Nutrition Optimization

**Mục tiêu:** Lựa chọn món và định lượng nguyên liệu để đạt mục tiêu dinh dưỡng.

Phương pháp:

- MILP sử dụng OR-Tools.
- Phương pháp đối chứng: GA hoặc heuristic.

Đầu vào: Điểm món, dữ liệu dinh dưỡng, mục tiêu và ràng buộc.

Đầu ra: Thực đơn và khối lượng nguyên liệu.

Chỉ số:

- Sai lệch calories.
- Sai lệch macro.
- Tỷ lệ tìm được thực đơn khả thi.
- Thời gian giải.
- Độ đa dạng thực đơn.

## M4. Feedback Learning

**Mục tiêu:** Cập nhật ưu tiên món ăn từ phản hồi.

Phương pháp dự kiến:

- LinUCB.
- Baseline random và epsilon-greedy.

Đầu vào: Ngữ cảnh gợi ý và phản hồi người dùng.

Đầu ra: Điểm ưu tiên được cập nhật.

Chỉ số: Cumulative Regret trên môi trường mô phỏng được định nghĩa.

---

# 7. GIAO DIỆN VÀ API DỰ KIẾN

## 7.1. Giao diện người dùng

Các màn hình dự kiến:

1. Nhập hồ sơ cá nhân.
2. Chọn mục tiêu và chế độ ăn.
3. Nhập sở thích, nguyên liệu cần tránh.
4. Xem nhu cầu năng lượng.
5. Xem thực đơn ngày hoặc tuần.
6. Xem chi tiết món và định lượng.
7. Quản lý thực phẩm có sẵn.
8. Danh sách đi chợ.
9. Ghi nhật ký ăn uống.
10. Đổi món và gửi phản hồi.

## 7.2. API

| Method | Endpoint | Chức năng |
|---|---|---|
| POST | `/api/parse` | Phân tích câu tiếng Việt |
| POST | `/api/energy` | Tính nhu cầu năng lượng |
| POST | `/api/plan` | Tạo thực đơn |
| GET | `/api/diets` | Lấy danh sách chế độ ăn |
| PUT | `/api/pantry` | Cập nhật thực phẩm có sẵn |
| GET | `/api/shopping-list` | Lấy danh sách đi chợ |
| POST | `/api/log` | Ghi nhật ký ăn uống |
| POST | `/api/feedback` | Gửi phản hồi món ăn |
| GET | `/api/dishes` | Xem danh mục món ăn |

Đây là các API dự kiến kế thừa từ tài liệu thiết kế. Request/Response Schema và mã lỗi sẽ được mô tả chi tiết trong tài liệu API Contract.

---

# 8. TIÊU CHÍ NGHIỆM THU

## 8.1. Nghiệm thu chức năng

- Người dùng nhập được hồ sơ hợp lệ.
- Hệ thống tính được TDEE và macro.
- Tạo được thực đơn ngày.
- Không sử dụng nguyên liệu bị cấm trong thực đơn.
- Hiển thị khối lượng nguyên liệu.
- Tạo danh sách đi chợ sau khi trừ lượng có sẵn.
- Ghi và lưu nhật ký ăn uống.
- Đổi món và ghi nhận phản hồi.

Các chức năng thực đơn tuần và cập nhật sở thích phải được kiểm tra theo phạm vi triển khai đã thống nhất.

## 8.2. Nghiệm thu ML

- Có baseline để so sánh.
- Có dữ liệu train/validation/test phù hợp.
- Có kết quả thực nghiệm thực tế.
- Có metric đánh giá cho từng mô-đun.
- Có báo cáo giải thích kết quả và giới hạn.
- Kết quả thực nghiệm có thể tái lập với cấu hình và dữ liệu đã công bố.

## 8.3. Nghiệm thu toàn hệ thống

Một luồng demo được coi là hoạt động khi:

1. Người dùng nhập hồ sơ.
2. Chọn mục tiêu và chế độ ăn.
3. Hệ thống tạo và hiển thị thực đơn.
4. Người dùng có thể xem định lượng và dinh dưỡng.
5. Người dùng đổi một món.
6. Hệ thống xử lý yêu cầu đổi món và cập nhật thực đơn.
7. Kết quả được lưu hoặc truy xuất lại theo thiết kế.

---

# 9. RỦI RO VÀ GIẢ ĐỊNH

## 9.1. Rủi ro

| ID | Rủi ro | Phương án |
|---|---|---|
| R01 | Thiếu dữ liệu đánh giá món Việt | Content-Based và thu thập phản hồi |
| R02 | Dataset Food.com khác dữ liệu Việt Nam | Đánh giá riêng từng nhánh gợi ý |
| R03 | Dữ liệu NLP ít | Mở rộng và kiểm tra nhãn |
| R04 | MILP không tìm được nghiệm | Thông báo, điều chỉnh ràng buộc mềm theo chính sách |
| R05 | Chậm tích hợp | Thống nhất API Contract từ sớm |
| R06 | Không đủ thời gian | Ưu tiên MVP và giảm phạm vi nâng cao |

## 9.2. Các vấn đề cần xác nhận

- Danh sách 4 thành viên và trách nhiệm chính.
- Phạm vi chức năng bắt buộc trong MVP.
- Cơ chế đăng ký, đăng nhập và quản lý tài khoản.
- Database Schema cuối cùng.
- Quy tắc ước lượng chi phí nguyên liệu.
- Cơ chế đánh giá món của người dùng mới.
- Cách xử lý thực đơn không đáp ứng đủ ràng buộc.
- Khả năng đáp ứng các ngưỡng hiệu năng.
- Cách đánh giá thực tế chất lượng gợi ý món Việt.

---

# 10. QUẢN LÝ THAY ĐỔI

Tài liệu SRS được quản lý bằng Git.

Các thay đổi quan trọng cần:

1. Có mô tả lý do.
2. Xác định các yêu cầu bị ảnh hưởng.
3. Đánh giá tác động đến Database, API, ML và Test Case.
4. Được nhóm thống nhất trước khi triển khai.
5. Cập nhật phiên bản tài liệu.

**Trạng thái phiên bản 1.0:** Bản nháp phục vụ phân tích, thiết kế và lập kế hoạch. Chưa được nghiệm thu chính thức.

---

# 11. TÀI LIỆU THAM CHIẾU

1. Đề cương đồ án `goi-y-thuc-don` phiên bản ban đầu.
2. Báo cáo tiến độ tuần 1, ngày 02/11–08/11/2026.
3. Tài liệu sơ đồ phân tích và thiết kế hệ thống.
4. Phiếu đăng ký và theo dõi đồ án môn Học máy nâng cao.
5. Repository tham khảo: https://github.com/hungnv-2811/goi-y-thuc-don

**Ghi chú:** SRS này được tái cấu trúc từ các yêu cầu và tài liệu nghiên cứu ban đầu. Các mục tiêu kỹ thuật chưa được triển khai hoặc xác minh không được xem là kết quả đã hoàn thành.
