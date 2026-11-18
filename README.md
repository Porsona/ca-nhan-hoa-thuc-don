# ca-nhan-hoa-thuc-don
Hệ thống đề xuất thực đơn món ăn Việt Nam dựa trên trí tuệ nhân tạo, sử dụng học máy, xử lý ngôn ngữ tự nhiên và tối ưu hóa dinh dưỡng để tạo ra các kế hoạch bữa ăn cá nhân hóa.
# 🍽️ Hệ thống gợi ý thực đơn cá nhân hóa

**Personalized Vietnamese Meal Recommendation System**

Đồ án môn Học máy nâng cao - Trường Đại học Xây dựng Hà Nội (HUCE).

## 1. Giới thiệu

Dự án xây dựng hệ thống gợi ý thực đơn món Việt dựa trên Machine Learning, Natural Language Processing (NLP) và tối ưu hóa dinh dưỡng.

Hệ thống hướng tới việc đề xuất món ăn phù hợp với sở thích, mục tiêu dinh dưỡng và các ràng buộc của người dùng.

## 2. Mục tiêu

- Phân tích yêu cầu ăn uống bằng tiếng Việt.
- Tính nhu cầu năng lượng BMR, TDEE và macronutrients.
- Gợi ý món ăn cá nhân hóa bằng Machine Learning.
- Tối ưu khẩu phần theo nhu cầu dinh dưỡng.
- Lập thực đơn theo ngày hoặc tuần.
- Ghi nhận phản hồi để cải thiện chất lượng gợi ý.

## 3. Kiến trúc dự kiến

1. NLP (PhoBERT): Phân tích yêu cầu người dùng.
2. Recommendation System: Content-Based và Collaborative Filtering.
3. Nutrition Optimization: MILP với Google OR-Tools.
4. Feedback Learning: Contextual Bandit (LinUCB).

Các công nghệ và mô hình sẽ được đánh giá tính khả thi trong quá trình triển khai.

## 4. Công nghệ dự kiến

- Language: Python
- Machine Learning: PyTorch, scikit-learn
- NLP: Hugging Face Transformers, PhoBERT
- Optimization: Google OR-Tools
- Backend: FastAPI
- Frontend: Streamlit
- Database: SQLite
- Version Control: GitHub

## 5. Dữ liệu dự kiến

- Food.com Recipes and Interactions.
- Bảng thành phần thực phẩm Việt Nam.
- Danh mục món ăn và công thức món Việt.
- Dữ liệu yêu cầu ăn uống tiếng Việt được gán nhãn.

## 6. Kế hoạch phát triển

| Tuần | Công việc |
|---|---|
| 1 | Phân tích nghiệp vụ, SRS, UML và thiết kế Database |
| 2 | Chuẩn bị dữ liệu, xây dựng baseline |
| 3 | Huấn luyện và phát triển mô hình |
| 4 | Tích hợp Backend, Frontend và Demo |
| 5 | Kiểm thử, đánh giá và hoàn thiện báo cáo |

## 7. Thành viên

Nhóm gồm 4 thành viên, phân công cụ thể sẽ được cập nhật.

## 8. Trạng thái

Các tính năng trong README là mục tiêu phát triển, chưa phải những chức năng đã hoàn thiện.

## 9. Tài liệu tham khảo

- [Repository nghiên cứu ban đầu](https://github.com/hungnv-2811/goi-y-thuc-don)
- [Food.com Dataset](https://www.kaggle.com/datasets/shuyangli94/food-com-recipes-and-user-interactions)
- [USDA FoodData Central](https://fdc.nal.usda.gov/)
