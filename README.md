# Phân tích các yếu tố tác động đến giá bất động sản TP.HCM

## Phạm vi
Nhà riêng trong bán kính 30 km quanh chợ Bến Thành (TP.HCM theo địa giới sau sáp nhập 2025; khoảng 18% mẫu thuộc Bình Dương cũ).

## Dữ liệu
- Ho Chi Minh City Real Estate Data 2025, Kaggle, tác giả Lâm Phú Cường: https://www.kaggle.com/datasets/cnglmph/ho-chi-minh-city-real-estate-data-2025
- Thu thập ngày 30/09/2025, license CC BY-NC 4.0
- `data/raw/data_public.csv`: dữ liệu gốc; `data/raw/metro_stations.csv`: 14 ga metro số 1

## Xử lý dữ liệu
51.304 tin → 4.490 căn sau khi lọc: chỉ giữ nhà riêng, có tọa độ hợp lệ, trong 30 km, giá 500 triệu – 200 tỷ, diện tích 10 – 1.000 m², bỏ 1% giá/m² hai đầu. Giá trị vô lý (số tầng, phòng ngủ, kích thước) chuyển thành ô trống rồi điền trung vị của tập train. Chi tiết từng bước trong `notebooks/cleaning.ipynb`.

## Cách chạy
```bash
pip install -r requirements.txt
```
Chạy lần lượt trong `notebooks/`: cleaning → EDA → ols → Random_Forest → Model_Comparison

## Cấu trúc thư mục
- `data/`: dữ liệu gốc (`raw/`) và đã làm sạch (`clean/`)
- `notebooks/`: làm sạch, phân tích, mô hình
- `report/`: hình và bảng kết quả