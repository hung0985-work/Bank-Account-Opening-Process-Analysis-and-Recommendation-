# Dự án phân tích và đề xuất quy trình mở tài khoản ngân hàng

## 1. Tổng quan dự án

Dự án này phân tích hành vi của khách hàng trong quy trình mở tài khoản số qua ứng dụng ngân hàng. Mục tiêu chính là xác định nguyên nhân khiến khách hàng rời bỏ quy trình onboarding, đánh giá các điểm nghẽn trong trải nghiệm người dùng và đề xuất cải tiến nhằm tăng tỷ lệ hoàn tất mở tài khoản.

Dữ liệu được phân tích trong dự án bao gồm hành trình mở tài khoản của 9.148 khách hàng trong 3 tháng đầu năm 2024, với các thông tin về trạng thái mở tài khoản, thời gian thao tác, thiết bị sử dụng, hệ điều hành, điểm rời bỏ và lý do bị từ chối.

## 2. Bối cảnh kinh doanh

Quy trình onboarding số là một trong những kênh quan trọng giúp ngân hàng thu hút khách hàng mới. Một quy trình mở tài khoản nhanh, dễ hiểu và ít lỗi có thể giúp ngân hàng tăng tỷ lệ chuyển đổi, giảm chi phí thu hút khách hàng và cải thiện trải nghiệm ban đầu.

Trong 3 tháng đầu năm 2024, ngân hàng thu hút hơn 9.000 khách hàng mở tài khoản và đạt tỷ lệ thành công 93%. Tuy nhiên, vẫn có hơn 600 khách hàng rời bỏ quy trình, gây ra tổn thất tiềm năng khoảng 4,8 tỷ đồng nếu tính theo chi phí thu hút khách hàng trung bình.

## 3. Mục tiêu phân tích

Dự án tập trung trả lời các câu hỏi chính:

- Khách hàng thường rời bỏ ở bước nào trong quy trình mở tài khoản?
- Các lỗi nào xuất hiện nhiều nhất trong hành trình onboarding?
- Nhóm khách hàng nào có khả năng rời bỏ hoặc gặp lỗi cao hơn?
- Thiết bị, hệ điều hành, độ tuổi và thời điểm thao tác có ảnh hưởng đến tỷ lệ thành công không?
- Có thể dự đoán khả năng khách hàng drop-off bằng mô hình học máy hay không?
- Ngân hàng nên cải thiện quy trình mở tài khoản theo hướng nào?

## 4. Phương pháp phân tích

Dự án sử dụng các phương pháp chính sau:

### 4.1. Làm sạch và xử lý dữ liệu

Dữ liệu được xử lý thông qua các bước như định dạng lại thời gian, xử lý dữ liệu thiếu, tạo biến mới, loại bỏ hoặc điều chỉnh các giá trị bất thường và chuẩn bị dữ liệu cho phân tích.

### 4.2. Phân tích khám phá dữ liệu

Phân tích khám phá dữ liệu được sử dụng để đánh giá tổng quan số lượng khách hàng, tỷ lệ mở tài khoản thành công, nhóm khách hàng chính, thiết bị sử dụng, thời gian thao tác và các điểm dừng trong quy trình.

### 4.3. Kiểm định Chi-square

Kiểm định Chi-square được sử dụng để đánh giá mối liên hệ giữa các yếu tố như nhóm tuổi, loại thiết bị với các lỗi quan trọng trong quy trình, đặc biệt là lỗi OTP và OCR.

### 4.4. Phân tích sống còn

Phân tích sống còn được sử dụng để đánh giá khả năng khách hàng tiếp tục hoặc rời bỏ quy trình theo từng nhóm đặc điểm, từ đó nhận diện nhóm có nguy cơ thất bại cao hơn.

### 4.5. Mô hình dự đoán

Dự án xây dựng hai nhóm mô hình dự đoán:

- Mô hình dự đoán khả năng khách hàng drop-off trong lần thử cuối cùng.
- Mô hình dự đoán khả năng khách hàng bị fail tại từng bước trong quy trình.

Các mô hình được thử nghiệm bao gồm XGBoost, LightGBM và Random Forest. Dữ liệu mất cân bằng được xử lý bằng SMOTE, sau đó mô hình được đánh giá bằng ROC-AUC, Accuracy, F1 Score, Precision và Recall.

## 5. Kết quả chính

Một số kết quả nổi bật của dự án:

- Ngân hàng có 9.148 khách hàng tham gia mở tài khoản trong 3 tháng đầu năm 2024.
- Có 8.543 khách hàng mở tài khoản thành công, tương ứng tỷ lệ thành công 93%.
- Hơn 600 khách hàng rời bỏ quy trình mở tài khoản.
- Trạng thái failed và pending chiếm tỷ lệ lớn trong hành vi của khách hàng, cho thấy quy trình onboarding vẫn còn nhiều điểm cần tối ưu.
- OCR và OTP là hai điểm nghẽn quan trọng nhất trong hành trình mở tài khoản.
- Lỗi OCR có tỷ lệ lặp lại cao nhất, cho thấy nhiều khách hàng bị mắc kẹt và phải thao tác nhiều lần tại bước này.
- Nhóm Baby Boomers có tỷ lệ fail cao hơn tại hai bước OCR và OTP.
- Nhóm khách hàng chính trong giai đoạn phân tích là nữ, thuộc Gen Y, sử dụng thiết bị Apple và hệ điều hành phiên bản mới.
- XGBoost là mô hình có ROC-AUC tốt nhất trong bài toán dự đoán khách hàng drop-off ở lần thử cuối cùng.

## 6. Cấu trúc file dự án

```text
Bank-Account-Opening-Process-Analysis/
│
├── Report.pdf
│   └── Báo cáo tổng hợp kết quả phân tích, bao gồm bối cảnh kinh doanh, xử lý dữ liệu, phân tích hiện trạng, nguyên nhân drop-off, mô hình dự đoán và đề xuất cải thiện.
│
├── Notebook 
│   └── File tổng hợp các Code được sử dụng trong dự án

```

## 7. Công cụ sử dụng

Dự án sử dụng các công cụ và thư viện chính sau:

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- LightGBM
- Random Forest
- SMOTE
- Chi-square test
- Survival Analysis
- PowerPoint / Canva cho phần trình bày báo cáo

## 8. Hạn chế của dự án

Dự án vẫn có một số hạn chế:

- Một số trường dữ liệu về nhân khẩu học và thiết bị có tỷ lệ thiếu khá cao.
- Cột lý do bị từ chối có tỷ lệ thiếu lớn, gây hạn chế trong việc phân tích chi tiết nguyên nhân thất bại.
- Dữ liệu thời gian có nhiều giá trị bất thường, cho thấy có thể tồn tại lỗi trong quá trình ghi nhận hoặc thu thập dữ liệu.
- Phạm vi dữ liệu chỉ bao gồm 3 tháng đầu năm 2024, chưa phản ánh đầy đủ hành vi khách hàng trong dài hạn.
- Mô hình dự đoán chỉ phản ánh mối quan hệ thống kê trong dữ liệu, không khẳng định quan hệ nhân quả tuyệt đối.

## 9. Đề xuất cải thiện

Dựa trên kết quả phân tích, ngân hàng nên ưu tiên các hướng cải thiện sau:

- Cải thiện bước OCR bằng cách hướng dẫn chụp ảnh rõ ràng hơn, bổ sung cảnh báo ảnh mờ, thiếu sáng hoặc sai khung hình.
- Tối ưu bước OTP bằng cách cải thiện giao diện nhập mã, nút gửi lại mã, thời gian đếm ngược và thông báo lỗi.
- Thiết kế lại các bước xác nhận quyền riêng tư và hợp đồng để khách hàng dễ nhìn thấy hành động cần thực hiện.
- Bổ sung hỗ trợ riêng cho nhóm khách hàng lớn tuổi, đặc biệt là nhóm Baby Boomers.
- Ưu tiên tối ưu ứng dụng trên iOS vì phần lớn khách hàng trong dữ liệu sử dụng thiết bị Apple.
- Sử dụng mô hình dự đoán để nhận diện sớm khách hàng có nguy cơ drop-off và kích hoạt hỗ trợ kịp thời.
- Theo dõi các khung giờ và ngày có lưu lượng mở tài khoản cao để đảm bảo hệ thống vận hành ổn định.

## 10. Hướng phát triển tiếp theo

Trong các phiên bản tiếp theo, dự án có thể được mở rộng theo các hướng:

- Xây dựng dashboard theo dõi funnel mở tài khoản theo thời gian thực.
- Tích hợp mô hình dự đoán drop-off vào hệ thống cảnh báo sớm.
- Bổ sung dữ liệu phản hồi khách hàng để hiểu rõ hơn các pain point trong trải nghiệm onboarding.
- Phân tích sâu hành vi sau khi mở tài khoản thành công, như nạp tiền, chuyển khoản hoặc sử dụng sản phẩm đầu tiên.
- Thiết kế A/B testing để đo lường hiệu quả của các cải tiến OCR, OTP và UI/UX.
