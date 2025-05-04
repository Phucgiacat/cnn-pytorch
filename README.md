# cnn-pytorch

Author: Bùi Hồng Phúc

---
### 1. Dataset.
Chúng ta đã quá quen sử dụng MNIST. MNIST là cở sở dữ liệu về chữ số viết tay, được sử dụng rất rộng rãi trong cộng đồng AI/ML. MNIST thường được thử đầu tiên khi có một thuật toán phân loại ảnh mới. Nhưng ngoài ra chúng ta còn có tập Fashion-MNIST được tạo ra gần đây có kích thước tương tự MNIST nhưng các ảnh là ảnh xám của trang phục các nhãn với các labels như sau:

<div align="center">

| idx | labels      |
|-----|-------------|
| 0   | T-shirt/top |
| 1   | Trouser     |
| 2   | Pullover    |
| 3   | Dress       |
| 4   | Coat        |
| 5   | Sandal      |
| 6   | Sneaker     |
| 7   | Bag         |
| 9   | Ankle boot  |

</div>
Fashion-MNIST có 6000 ảnh cho training, 10000 ảnh cho test. mỗi ãnh có kích thướng có thể xem trực quan như sau:

<p align="center">
  <img src="image\images_fashion.png" alt="Deslant minh hoạ" width="300"/>
</p>
bên trên là nội dung của 64 ảnh trắng đen của các loại ảnh bạn có thể xem nó một các trực quan nhất.

### 2. Cấu trúc mô hình
ở phần này ta chỉnh thực hiện bằng cấu trúc đơn giản ta sẽ thực hiện theo cấu trúc như sau:
> Conv2d $\rightarrow$ ReLU $\rightarrow$ MaxPool2d $\rightarrow$ Conv2d $\rightarrow$ ReLU $\rightarrow$ MaxPool2d $\rightarrow$ Linear $\rightarrow$ ReLU $\rightarrow$ Linear $\rightarrow$ ReLU $\rightarrow$ Linear $\rightarrow$ Adam.

Với cấu trúc này sẽ được định nghĩa bên trong class:
> Net(nn.Model)

### 3. quy trình train.
Phần này sẽ được thực hiện tuần tự và mỗi lần sẽ được train trên 1 batch với `batch_size=64` và ở đây `accuracy` sẽ được đánh giá dựa vào tập test qua nhiều lần test thì số `epoch=10` thì sẽ khá hiệu quả.

Sau mỗi lần train sẽ thu được kết quả như sau:

| Epoch     |Loss       |accuracy   |f1     |
|:----------|:----------|:----------|:------|
|1/10       |0.5346     |0.8533     |0.8524 |
|2/10       |0.3601     |0.8586     |0.8585 |
|3/10       |0.3166     |0.8763     |0.8764 |
|4/10       |0.2894     |0.8784     |0.8795 |
|5/10       |0.2728     |0.8871     |0.8862 |
|6/10       |0.2551     |0.8898     |0.8891 |
|7/10       |0.2455     |0.8896     |0.8888 |
|8/10       |0.2342     |0.8944     |0.8949 |
|9/10       |0.2236     |0.8943     |0.8932 |
|10/10      |0.2165     |0.8981     |0.8981 |

Ta có thể cảm nhận được sau 10 lần train thì đạt được kết quả khá tốt với `accuracy=0.8981` tại `epoch=10` có thể train thêm.

### 4. Kiểm tra trên tập test.
khi kiếm tra trên tập test ta có thể nhận thấy thông qua ma trận confusion:
<p align="center">
  <img src="image\confusion.png" alt="Deslant minh hoạ" width="300"/>
</p>

---
$$
end
$$
Sẽ có thêm một số cải tiến cho mô hình. Tài liệu tham khảo:
[Xây dựng mạng CNN bằng pytorch](https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html)
[pytorch cơ bản](https://phamdinhkhanh.github.io/2019/08/10/PytorchTurtorial1.html#39-hu%E1%BA%A5n-luy%E1%BB%87n-model-tr%C3%AAn-gpu)