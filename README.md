# Nhận Diện Cử Chỉ Tay (Hand Sign Recognition)

Dự án này ứng dụng Trí tuệ Nhân tạo và Machine Learning để nhận diện các trạng thái/cử chỉ tay. Dự án sử dụng **MediaPipe** để tự động phát hiện và trích xuất tọa độ các khớp tay (landmarks) thông qua camera, sau đó sử dụng mạng Nơ-ron nhân tạo của **TensorFlow/Keras** để phân loại dự đoán loại cử chỉ đó.

## Cấu trúc hệ thống

*   **`/models/`**: Thư mục lưu trữ các mô hình Neural Network đã được huấn luyện xong (thường ở định dạng `.h5`).
*   **`/train/`**: Chứa các file Jupyter Notebook dùng để tiến hành huấn luyện các mô hình. Tại đây, dữ liệu được tiền xử lý và đưa vào mạng học sâu.
*   **`/test/`**: Chứa các file để chạy đánh giá và kiểm thử dự đoán mô hình ngoài thực tế với camera.
*   **`lay_toa_do.ipynb`**: Công cụ trích xuất dữ liệu. Máy sẽ quét bàn tay thông qua camera/ảnh, lấy ra 21 điểm mốc (hand landmarks) và lưu lại dưới dạng dữ liệu dạng bảng.
*   **`toadotay1.csv`**: Tập dữ liệu (dataset) ví dụ về các tọa độ tay đã được thu thập, là nguyên liệu chính để huấn luyện mô hình.
*   **`requirements.txt`**: Tệp kê khai chi tiết các gói thư viện Python cần thiết (kèm đúng phiên bản gốc) sao cho môi trường chạy không bị lỗi tương thích.

## Các Công Nghệ Chính
*   **TensorFlow & Keras (\>= 2.10.0)**: Thư viện Machine Learning cốt lõi để tạo mô hình phân loại.
*   **MediaPipe (\>= 0.10.9)**: Công nghệ của google mạnh mẽ cho việc phát hiện và map các điểm ảnh trên bàn tay tốc độ cao.
*   **OpenCV (`opencv-python` \>= 4.11.0)**: Bắt kích và xử lý luồng Video/Camera cũng như hình ảnh.
*   **Scikit-learn, Pandas, Numpy**: Nhóm thư viện phân tích và xử lý tập dữ liệu CSV trước khi đưa vào mô hình.

## Cách Cài Đặt

Dự án này sử dụng môi trường ảo (virtual environment). Để cài đặt nhanh tất cả thư viện với đúng phiên bản đang hoạt động bình thường, hãy chạy lệnh dưới đây trong Terminal / CMD (bạn nhớ kích hoạt `venv` trước nhé):

```bash
pip install -r requirements.txt
```

## Các Bước Chạy Dự Án (Luồng Làm Việc)

1.  **Lấy Dữ Liệu**: Mở `lay_toa_do.ipynb`, khởi động camera và thực hiện các động tác tay tương ứng để tự động ghi các tọa độ tạo thành tập dữ liệu `.csv`.
2.  **Huấn Luyện (Training)**: Vào thư mục `train/`, mở các file `train_handsign...ipynb` để nạp file `.csv`. Cấu hình model và tiến hành fit để train model. Model tốt nhất sẽ xuất ra thư mục `models/`.
3.  **Sử Dụng & Kiểm Thử (Testing)**: Vào `test/`, chạy các file script để hệ thống load mô hình `.h5` lên, lấy dữ liệu trực tiếp từ MediaPipe qua realtime Camera và hiển thị kết quả phân loại lên màn hình.
