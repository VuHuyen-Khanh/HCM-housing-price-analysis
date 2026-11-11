# Phân tích các yếu tố tác động đến giá bất động sản TP.HCM

# Phạm vi
- Nhà riêng tại TP.HCM theo địa giới sau sáp nhập (2025), trong bán kính 30 km quanh chợ Bến Thành.


## Dữ liệu
- Tên bộ dữ liệu: Ho Chi Minh City Real Estate Data 2025
- Nguồn: Kaggle, tác giả Lâm Phú Cường (cnglmph), link: https://www.kaggle.com/datasets/cnglmph/ho-chi-minh-city-real-estate-data-2025 
- Ngày thu thập: 30/09/2025
- License: CC BY-NC 4.0 (Attribution-NonCommercial 4.0 International), https://creativecommons.org/licenses/by-nc/4.0/
- File gốc: `data/raw/data_public.csv`

## Quy trình lọc dữ liệu
Bước - Nội dung - Số dòng còn lại |
B1 - Đọc dữ liệu gốc - 51.304 |
B2 - Bỏ tin trùng (theo Listing ID), không có tin trùng - 51.304 |
B3 - Chỉ giữ Nhà riêng - 8.184 | 
B4 - Có tọa độ - 5.137 |
B5 - Tọa độ hợp lệ - 5.121 | 
B6 - Trong 30 km quanh chợ Bến Thành - 4.671 
B7 - Giá 500 triệu -> 200 tỷ, diện tích 10 -> 1.000 m² - 4.582 |
B8 - Bỏ 1% giá/m² thấp nhất và 1% cao nhất - 4.490

## Xử lý thiếu dữ liệu 
- Bỏ 4 cột thiếu trên 50%: Bathrooms, Direction, Alley Width, Road Type
- Chia train/test 80/20 (3.592 / 898 dòng), random_state=42
- Điền ô trống cột số (Width, Length, Bedrooms, Floors) bằng trung vị của tập train; cột Position điền "Không rõ"
- Biến mục tiêu: Log_Price_per_m2. Có thêm Dist_BenThanh_km và Dist_Metro_km (ga metro số 1 gần nhất)

## Lưu ý về phạm vi dữ liệu
- Khoảng 18% mẫu thuộc các phường Bình Dương cũ (nay nằm trong TP.HCM). Kết quả vì vậy phản ánh vùng TP.HCM mở rộng, không riêng TP.HCM cũ

## Cấu trúc thư mục

- `data/raw/`: dữ liệu gốc và danh sách ga metro
- `data/clean/`: dữ liệu đã làm sạch (`clean_1.csv`, `train.csv`, `test.csv`)
- `notebooks/`: notebook làm sạch, phân tích, mô hình
- `report/`: báo cáo và slide