# Digital-Marketing-Campaign-Analysis-and-Prediction
## CONTEXT
Công ty đang triển khai nhiều chiến dịch quảng cáo trên các nền tảng khác nhau như social media, email và search. Mỗi ngày, hàng nghìn người dùng mới tương tác với quảng cáo và truy cập vào website.
Tuy nhiên, việc đánh giá hiệu quả của một chiến dịch thường chỉ có thể thực hiện sau khi khách hàng hoàn tất hành vi mua hàng. Điều này dẫn đến độ trễ trong việc ra quyết định, khiến công ty tiếp tục chi tiêu ngân sách cho những quảng cáo không hiệu quả trong một khoảng thời gian dài.
Trong bối cảnh chi phí quảng cáo ngày càng tăng, công ty cần một cách tiếp cận chủ động hơn để đánh giá chất lượng người dùng và hiệu quả chiến dịch ngay từ giai đoạn đầu.
## NEEDS (Nhu cầu)
Công ty cần một phương pháp để:
Xác định sớm những người dùng có khả năng chuyển đổi cao hoặc thấp
Đánh giá hiệu quả của từng chiến dịch quảng cáo trước khi kết thúc
Giảm thiểu chi phí lãng phí cho các quảng cáo không mang lại giá trị
Hiện tại, các chỉ số như Click-Through Rate (CTR) hoặc số lượt truy cập chưa đủ để phản ánh chính xác khả năng chuyển đổi của người dùng. Vì vậy, cần một hệ thống đánh giá tốt hơn dựa trên hành vi thực tế của khách hàng.

## VISION (Giải pháp)
Xây dựng một mô hình machine learning nhằm dự đoán xác suất chuyển đổi (P(convert)) của từng người dùng dựa trên:
Hành vi trên website (số lần truy cập, thời gian ở lại, số trang xem)
Mức độ tương tác với quảng cáo (CTR, email clicks, social shares)
Thông tin khách hàng (thu nhập, lịch sử mua hàng, loyalty)
Sau đó, kết hợp xác suất chuyển đổi với giá trị vòng đời ước tính (LTV) và chi phí quảng cáo (AdSpend) để tính toán Expected Value (EV):
Nếu EV < 0 → đề xuất dừng quảng cáo
Nếu EV > 0 → tiếp tục hoặc tăng ngân sách.

## OUTCOME (Kết quả mong đợi)
Sau khi triển khai, công ty có thể:
Đánh giá chất lượng người dùng chỉ sau một khoảng thời gian ngắn
Giảm chi tiêu cho các chiến dịch kém hiệu quả
Tăng ROI bằng cách tập trung ngân sách vào các nhóm khách hàng có giá trị cao
Ngoài ra, hệ thống sẽ được kiểm tra định kỳ bằng cách so sánh xác suất dự đoán với kết quả thực tế nhằm đảm bảo độ tin cậy của mô hình.
Về lâu dài, giải pháp này giúp công ty chuyển từ cách vận hành bị động sang chủ động, tối ưu hóa hiệu quả marketing dựa trên dữ liệu.

## Approach (Pipeline)
The solution follows a data-driven pipeline:
Data preprocessing and cleaning to ensure data quality.

Feature engineering from user behavior, marketing interaction, and customer profile.

Training a classification model (Logistic Regression / XGBoost) to predict conversion probability.

Applying probability calibration to ensure predicted probabilities reflect real-world outcomes.

Estimating customer Lifetime Value (LTV) using proxy features such as income and past purchases.

Calculating Expected Value (EV) by combining predicted conversion probability, LTV, and advertising cost.

Making decisions to continue or stop campaigns based on EV.

## Decision Logic
The core decision is based on Expected Value (EV):

EV=P(convert)×LTV−Cost

If EV > 0 → Continue or increase ad spend
If EV < 0 → Stop the campaign to avoid losses
This ensures that decisions are not based solely on prediction accuracy, but on financial impact.
