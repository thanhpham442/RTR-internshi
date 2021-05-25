<img src="./images/RtR_footage.png" width="100%">

# Plan: GEO tag power line

## Detailed Plan

|Num|Task                         |Source  |Reference|Note|Assignee |Day|Week|Progress|
|-|-----------------------------|--------|---------|----|------|----|--|--------|
|1|Chạy lại ví dụ về mạng SegNet Jetson Inference|[file]()|[jetson inference segnet](https://github.com/dusty-nv/jetson-inference)|Ghi chú lại `mAP` và `FPS`|`Quân`|13/3/2021|1|:white_check_mark:|
|2|Tìm hiểu source UNet TensorRT|[file]()|[unet keras](https://github.com/vietanhdev/unet-uff-tensorrt), [unet pytorch](https://github.com/milesial/Pytorch-UNet), [unet to onnx](https://blog.csdn.net/hello_dear_you/article/details/109744627), [unet brain sgementation](https://github.com/mateuszbuda/brain-segmentation-pytorch), [unet jetson](https://forums.developer.nvidia.com/t/deep-learning-inference-benchmarking-instructions/73291)|Đọc cách có thể train lại với custom dataset|`Quân`|13/3/2021|1||
|3|Chạy thử lại source UNet TensorRT|[file]()|[link](https://github.com/vietanhdev/unet-uff-tensorrt)|Ghi chú lại `mAP` và `FPS`|`Quân`|13/3/2021|1||
|4|So sánh SegNet Jetson Inference và Unet TensorRT|[file]()|[link]()|So sánh `mAP` và `FPS` thực nghiệm của hai phương pháp. Chốt phương án.|`Quân`|13/3/2021|1|
|5|Tìm hiểu về Docker|[file]()|[link](https://www.docker.com/)|Công cụ cho phép cài đặt thư viện tiện lợi cho nhiều lần|`Quân`|13/3/2021|1||
|6|Thiết lập Jetson Nano|[file]()|[link](https://developer.nvidia.com/embedded/learn/tutorials/jetson-container)|Tạo Docker chứa các thư viện cần thiết cho Jetson Nano để có thể chạy dự án này|`Quân`|13/3/2021|1||
|7|Tìm hiểu cách training lại mã nguồn với custom dataset|[file]()|[link]()|So sánh thời gian train ở máy `PC` và `Google Colab`|`Quân`|20/3/2021|2||
|8|Xử lý dataset về format COCO |[file]()|[link](https://github.com/r3ab/ttpla_dataset) |Fix lỗi trường `data image` bị mã hóa|`Quân`| 20/3/2021    |2||
|9|Cài đặt các thư viện cần thiết cho máy PC Local để train|[file]()|[link]()|Tạo file `docker` backup|`Quân`|20/3/2021|2||
|10|Training model GEO tag power line|[file]()|[link]()|Viết lại quy trình train|`Quân`|20/3/2021|2||
|11|Đánh giá kết quả training và chọn model để test|[file]()|[link]()|Đánh giá model dựa vào biểu đồ hàm `Loss`. Vẽ các biểu đồ liên quan|`Quân`|20/3/2021|2||
|12|Chuyển đổi model sang dạng TensorRT để chạy trên Jetson Nano|[file]()|[link]()|Format của model ở dạng `.onnx`|`Quân`|20/3/2021|2||
|13|Test model GEO tag power line trên Jetson Nano|[file]()|[link]()|Ghi chú lại kết quả về `mAP` và `FPS`|`Quân`|27/3/2021|3||
|14|Đánh giá kết quả model khi chạy trên Jetson Nano|[file]()|[link]()|Kết quả về các tiêu chí sau: `FPS`, `mAP`, `Computer Cost`|`Quân`|27/3/2021|3||
|15|Tìm hiểu Deep Stream|[file]()|[link 1](https://developer.nvidia.com/deepstream-sdk), [link 2](https://github.com/Azure-Samples/NVIDIA-Deepstream-Azure-IoT-Edge-on-a-NVIDIA-Jetson-Nano), [link 3](https://github.com/vortextemporum/DeepStream-Loves-Osc)|Ghi lại `.doc` cách sử dụng Deep Stream|`Quân`|27/3/2021|3||
|16|Vẽ Flowchart của module GEO tag power line tích hợp với Deep Stream|[file]()|[link]()|Cần đưa ra Flowchart để tối ưu thuật toán và đưa ra list các hàm cần thiết|`Quân`|27/3/2021|3||
|17|Code tích hợp model GEO tag power line với Deep Stream|[file]()|[link]()|Code phân tách ra từng Module|`Quân`|27/3/2021|3||
|18|Đánh giá kết quả model GEO tag power line chạy với nền tảng Deep Stream|[file]()|[link]()|Ghi lại `FPS`, `Computer Cost`|`Quân`|27/3/2021|3||
|19|Code module GEO tag power line phát hiện đường dây điện|[file]()|[link]()|Code theo dạng file và class để có thể dễ dàng import vào `VIAN SIGHT`|`Quân`|3/4/2021|4||
|20|Vẽ Flowchart tích hợp Geo tag power line (Deep Stream) với module `VIAN SIGHT`|[file]()|[link]()|Đưa ra Flowchart và lưu đồ thuật toán phù hợp với module anh `Khôi` đã phát triển|`Quân`|3/4/2021|4||
|21|Tích hợp code module GEO tag power line vào `VIAN SIGHT`|[file]()|[link]()|Tích hợp với module `VIAN SIGHT` đã phát triển của anh Khôi|`Quân`|3/4/2021|4||
|22|Debug đợt 1|[file]()|[link]()|Sửa các lỗi cơ bản|`Quân`|3/4/2021|4||
|23|Tối ưu chương trình khi tích hợp vào máy bay `Vian`|[file]()|[link]()|Tối ưu về tốc độ và hiệu năng của chương trình|`Quân`|10/4/2021|5||
|24|Debug đợt 2|[file]()|[link]()|Sửa các lỗi khi tích hợp với hệ thống của `Vian`|`Quân`|10/4/2021|5||
|25|Clean code|[file]()|[link]()|Làm sạch code, phân bổ riêng các module và sắp xếp lại thứ tự các lệnh cho khoa học|`Quân`|10/4/2021|5||
|26|Đóng gói code|[file]()|[link]()|Đóng gói phiên bản v.01 bao gồm: `code`, `doc`, `fowchart`, `docker image`, `manual`.|`Quân`|10/4/2021|5||
|27||[file]()|[link]()||`Quân`|10/4/2021|5||







