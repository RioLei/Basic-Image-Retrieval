# Basic-Image-Retrieval
Xây dựng một chương trình cho phép truy vấn hình ảnh sử dụng các phép đo độ tương đồng giữa các hình ảnh (Similarity Measure).

- **Input**: Hình ảnh truy vấn q và bộ dữ liệu C.
- **Output**: Danh sách các hình ảnh c (c ∈ C) có sự tương quan đến hình ảnh truy vấn.

<img width="459" alt="image" src="https://user-images.githubusercontent.com/88385496/198692020-95495c2c-725f-4fd6-b850-7d1bc13238f0.png">
<img width="475" alt="image" src="https://user-images.githubusercontent.com/88385496/198692288-83307a4c-32cc-4fcd-8321-e323eab72ac4.png">

## Download dataset
> Data đã được xử lý, tải [tại đây](https://drive.google.com/file/d/1bPADa_yqvDENnNiRLq__GFn4DrUTt_NY/view?usp=sharing). Chuyển sang step 4 

## Step 1: Crawl urls chứa ảnh từ web về, lưu thành file txt.
Gửi request đến trang freeimages.com, lưu các đường dẫn của ảnh vào file txt theo từng topic.

`python utils/crawl_urls_to_txts.py` 

## Step 2: Lấy ảnh từ file txt đã crawl từ step 1.
Tải các hình ảnh theo từng topic vào các thư mục với tên tương ứng với từng topic

`python utils/get_images_from_txts.py`

## Step 3: Tiền xử lý các file ảnh ở step 2.
- Loại bỏ những hình ảnh lỗi (Không đọc được ảnh,...)

- Loại bỏ những hình ảnh có kích thước nhỏ hơn 10

- Loại bỏ hình ảnh có channel khác 3 (chỉ nhận ảnh màu RGB)

`python utils/preprocessingData.py`

## Step 4: 
- Lưu data đã được xử lý vào folder static/images
- Tải [weight_resnet50](https://drive.google.com/file/d/1MGnNmnh7evfATsSSJTWcB-IPE36IVZ40/view?usp=share_link)
- Sau đó chạy file feature_extractor.py để trích xuất feature tập dataset. Sau khi chạy xong thu được 1 file tại feature/all_features.npz 

`python feature_extractor.py`

## Step 5: 
- Run web: [](http://localhost:6868/)
`python app.py`

# Demo website
- Giao diện của web
<img width="1080" alt="image" src="https://user-images.githubusercontent.com/88385496/198829340-565d3b87-8ce5-4536-8f9c-f9b80c11b434.png">

- Upload ảnh
<img width="1080" alt="image" src="https://user-images.githubusercontent.com/88385496/198829382-bb520312-9433-4545-9dee-93a922bc5fdb.png">

- Kết quả 
<img width="1063" alt="image" src="https://user-images.githubusercontent.com/88385496/198829405-6812e96f-a5b3-48f2-90f8-1d895dae033d.png">

