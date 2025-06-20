---
title: "Data Structure Delving into List"
datePublished: Tue Jun 17 2025 03:43:04 GMT+0000 (Coordinated Universal Time)
cuid: cmbzz9zhy000u02jp10kr4yw8
slug: data-structure-delving-into-list

---

## **I. Giới thiệu về Data Structure và List**

### **Khái niệm Cấu trúc Dữ liệu**

Cấu trúc dữ liệu là phương thức tổ chức và lưu trữ dữ liệu trong máy tính để có thể truy cập và sử dụng một cách hiệu quả. Trong Python, cấu trúc dữ liệu được chia thành hai loại chính: Built-in Data Structures (List, Dictionary, Tuple, Set) và User-Defined Data Structures (Stack, Queue, Tree, Linked List, Graph).

### **Đặc điểm của List trong Python**

List là một cấu trúc dữ liệu **mutable (có thể thay đổi)**, **ordered (có thứ tự)** và **cho phép chứa các phần tử trùng lặp**. Các đặc điểm quan trọng của List bao gồm:

* **Ordered**: Các phần tử có thứ tự xác định và thứ tự này không thay đổi trừ khi có can thiệp.
    
* **Changeable**: Có thể thay đổi, thêm, xóa phần tử sau khi tạo.
    
* **Allow Duplicates**: Cho phép các phần tử có giá trị giống nhau.
    
* **Dynamic Size**: Kích thước có thể thay đổi trong quá trình thực thi
    

## **II. 1D List - Mảng Một Chiều**

### **Tạo và Khởi tạo List**

List được tạo bằng cách sử dụng dấu ngoặc vuông `[]` và các phần tử được phân cách bởi dấu phẩy:

```python
# Tạo list rỗng
empty_list = []

# List số tự nhiên
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# List hỗn hợp nhiều kiểu dữ liệu
mixed_list = [True, 5, 'some string', 123.45]

# List lồng nhau
nested_list = ["Happy", [2, 0, 1, 5]]

# List thực tế
shopping_list = ['táo', 'chuối', 'cherries', 'dâu', 'mận']
```

### **Indexing và Slicing**

List trong Python hỗ trợ cả forward indexing (bắt đầu từ 0) và backward indexing (bắt đầu từ -1)

```python
data = [4, 5, 6, 7, 8, 9]

# Forward indexing
print(data[0])    # Output: 4
print(data[3])    # Output: 7

# Backward indexing  
print(data[-1])   # Output: 9
print(data[-3])   # Output: 7

# Slicing: list[start:end:step]
print(data[2:4])  # Output: [6, 7]
print(data[3:])   # Output: [7, 8, 9]
print(data[:3])   # Output: [4, 5, 6]
```

### **Các Phép toán Cơ bản**

List hỗ trợ các phép toán **nối (+)** và **nhân (\*)** để tạo list mới:

```python
data1 = [6, 5, 7]
data2 = [1, 9, 2]

# Nối hai list
combined = data1 + data2  # [6, 5, 7, 1, 9, 2]

# Nhân list với số nguyên
repeated = data1 * 3      # [6, 5, 6, 5, 6, 5]
```

### **Phương thức Built-in**

List cung cấp nhiều phương thức hữu ích để **thao tác dữ liệu**:

```python
data = [6, 5, 7, 1, 9, 2]

# Thêm phần tử
data.append(4)           # Thêm vào cuối
data.insert(0, 4)        # Thêm vào vị trí chỉ định
data.extend([9, 2])      # Thêm nhiều phần tử

# Cập nhật phần tử
data[1] = 4              # Thay đổi giá trị tại index 1

# Xóa phần tử
data.pop(2)              # Xóa theo index
data.remove(5)           # Xóa theo giá trị
del data[1:3]            # Xóa nhiều phần tử
data.clear()             # Xóa tất cả

# Sắp xếp và đảo ngược
data.sort()              # Sắp xếp tăng dần
data.sort(reverse=True)  # Sắp xếp giảm dần
data.reverse()           # Đảo ngược thứ tự
```

### **Built-in Functions cho List**

Python cung cấp **nhiều hàm built-in** để xử lý List:

```python
data = [6, 5, 7, 1, 9, 2]

length = len(data)        # Độ dài: 6
minimum = min(data)       # Giá trị nhỏ nhất: 1
maximum = max(data)       # Giá trị lớn nhất: 9
total = sum(data)         # Tổng: 30

# Sắp xếp không thay đổi list gốc
sorted_data = sorted(data)           # Tăng dần
sorted_desc = sorted(data, reverse=True)  # Giảm dần
```

### **List Comprehension**

**List comprehension** cho phép tạo list mới một cách ngắn gọn và hiệu quả:

```python
# Cú pháp cơ bản: [expression for item in iterable if condition]

# Bình phương các số
squares = [x**2 for x in range(1, 11)]  # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# Với điều kiện
even_squares = [x**2 for x in range(1, 11) if x % 2 == 0]  # [4, 16, 36, 64, 100]

# Với mệnh đề if-else
data = [1, 5, -4, 3, -2]
relu_values = [x if x > 0 else 0 for x in data]  # [1, 5, 0, 3, 0]
```

## **III. 2D List - Mảng Hai Chiều**

### **Khái niệm và Ứng dụng**

**2D List** là cấu trúc dữ liệu **hai chiều** được sử dụng để **biểu diễn dữ liệu dạng bảng, ma trận hoặc lưới**. Trong thực tế, **2D List** được ứng dụng rộng rãi trong:

* **Ma trận toán học**: Tính toán đại số tuyến tính.
    
* **Digital Images**: Biểu diễn pixel và xử lý ảnh.
    
* **Game Development**: Bàn cờ, lưới game.
    
* **Data Analysis**: Bảng dữ liệu và spreadsheet.
    

### **Tạo và Truy cập 2D List**

```python
# Tạo 2D List
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# Truy cập phần tử: matrix[row][column]
print(matrix[0][0])  # Output: 1
print(matrix[1][1])  # Output: 5
print(matrix[2][2])  # Output: 9

# Kích thước ma trận
num_rows = len(matrix)      # 3 hàng
num_cols = len(matrix[0])   # 3 cột
```

### **Duyệt qua 2D List**

Có hai cách chính để duyệt qua 2D List:

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# Phương pháp 1: Sử dụng for-in
for row in matrix:
    for element in row:
        print(element, end=' ')
    print()

# Phương pháp 2: Sử dụng index
num_rows = len(matrix)
num_cols = len(matrix[0])
for r in range(num_rows):
    for c in range(num_cols):
        print(matrix[r][c], end=' ')
    print()
```

### **Cập nhật và Thao tác 2D List**

```python
# Cập nhật phần tử
matrix[1][1] = 0  # Thay đổi giá trị tại hàng 1, cột 1

# Tạo 2D List với kích thước xác định
rows, cols = 3, 3
matrix = [[0 for j in range(cols)] for i in range(rows)]
```

### **Hadamard Product (Phép nhân Element-wise)**

**Hadamard Product** là phép **nhân từng phần tử** tương ứng của hai ma trận:

```python
# Hadamard Product
G = [[3, 5, 7], [4, 9, 8]]
H = [[1, 6, 3], [0, 2, 9]]

num_rows = len(G)
num_cols = len(G[0])
result = [[0]*num_cols for _ in range(num_rows)]

for r in range(num_rows):
    for c in range(num_cols):
        result[r][c] = G[r][c] * H[r][c]

# Result: [[3, 30, 21], [0, 18, 72]]
```

## **IV. Algorithms trên List**

### **Linear Search Algorithm**

**Linear Search** là thuật toán tìm kiếm cơ bản nhất, kiểm tra từng phần tử một cách tuần tự từ đầu đến cuối list.

![Minh họa thuật toán Linear Search](https://pplx-res.cloudinary.com/image/upload/v1749913546/pplx_code_interpreter/dbda88c4_yxr7fd.jpg align="left")

**Cài đặt Linear Search:**

```python
def linear_search(data, target):
    """
    Thuật toán tìm kiếm tuyến tính
    Độ phức tạp: O(n)
    """
    for i in range(len(data)):
        if data[i] == target:
            return i  # Trả về index của phần tử tìm thấy
    return -1  # Không tìm thấy

data = [6, 5, 7, 1, 9, 2]
print(linear_search(data, 9))  # Output: 4
print(linear_search(data, 8))  # Output: -1
```

**Đặc điểm Linear Search:**

* **Độ phức tạp thời gian**: O(n) trong trường hợp xấu nhất.
    
* **Độ phức tạp không gian**: O(1).
    
* **Ưu điểm**: Đơn giản, hoạt động với mọi loại dữ liệu.
    
* **Nhược điểm**: Chậm với dữ liệu lớn.
    

### **Sorting Algorithms**

**Simple Sorting sử dụng min(), remove(), append()**

```python
def simple_sort(data):
    """
    Thuật toán sắp xếp đơn giản
    Độ phức tạp: O(n²)
    """
    data_copy = data.copy()
    result = []
    
    while data_copy:
        min_value = min(data_copy)
        result.append(min_value)
        data_copy.remove(min_value)
    
    return result
```

### **So sánh độ phức tạp các Thuật toán Sắp xếp (Sorting algorithm)**

**Độ phức tạp Thuật toán**

Độ phức tạp thuật toán là thước đo hiệu suất của thuật toán theo kích thước đầu vào:

![Biểu đồ so sánh độ phức tạp các thuật toán](https://pplx-res.cloudinary.com/image/upload/v1749913372/pplx_code_interpreter/3b91d8a1_vgkimc.jpg align="left")

**Các loại độ phức tạp phổ biến:**

* **O(1)**: Constant time - Thời gian hằng số.
    
* **O(log n)**: Logarithmic time - Tìm kiếm nhị phân.
    
* **O(n)**: Linear time - Linear search.
    
* **O(n log n)**: Linearithmic time - Merge sort, Quick sort.
    
* **O(n²)**: Quadratic time - Bubble sort, Insertion sort.
    
* **O(2^n)**: Exponential time - Brute force algorithms.
    

## **V. Kiến thức Mở rộng**

### **Activation Functions trong Neural Networks**

**Hàm Sigmoid**

**Hàm Sigmoid** là một trong những hàm kích hoạt quan trọng nhất trong neural networks:

**Công thức toán học: σ(x)=1/e^(-x)**

**Đặc điểm:**

* **Domain**: (-∞, +∞)
    
* **Range**: (0, 1)
    
* **Tính chất**: Monotonic, continuous, differentiable
    
* **Đạo hàm**: σ'(x) = σ(x)(1 - σ(x))
    

```python
import math

def sigmoid(x): #Hàm Sigmoid
    return 1 / (1 + math.exp(-x))

def sigmoid_for_list(data): #Áp dụng sigmoid cho list
    return [sigmoid(x) for x in data]

data = [1, 5, -4, 3, -2]
result = sigmoid_for_list(data)
# Output: [0.731, 0.993, 0.018, 0.953, 0.119]
```

### **Hàm ReLU**

ReLU (Rectified Linear Unit) là hàm kích hoạt phổ biến nhất trong deep learning hiện đại:

**Công thức toán học:**  
ReLU(x) = max⁡(0,x) = {

```python
def relu(x): #Hàm ReLU
    return max(0, x)

def relu_for_list(data): #Áp dụng ReLU cho list
    return [relu(x) for x in data]

def relu_list_comprehension(data): # Sử dụng List Comprehension
    return [x if x > 0 else 0 for x in data]

data = [1, 5, -4, 3, -2]
result = relu_list_comprehension(data)
# Output: [1, 5, 0, 3, 0]
```

![Biểu đồ minh họa hàm Sigmoid và ReLU](https://pplx-res.cloudinary.com/image/upload/v1749913469/pplx_code_interpreter/a553ade9_qhskd2.jpg align="left")

Biểu đồ minh họa hàm Sigmoid và ReLU

**Ưu điểm của ReLU:**

* Giải quyết vấn đề vanishing gradient
    
* Tính toán nhanh và đơn giản
    
* Thúc đẩy sparsity trong neural networks
    

### **Prefix Sum Array Technique**

**Prefix Sum Array** (hay Integral Array) là kỹ thuật **tối ưu hóa** quan trọng cho việc tính tổng trong đoạn:

![Minh họa Prefix Sum Array (mảng tổng tiền tố)](https://pplx-res.cloudinary.com/image/upload/v1749913629/pplx_code_interpreter/7ba0d467_lycigg.jpg align="left")

**Khái niệm:**  
**Prefix Sum Array** là mảng mà **mỗi phần tử tại vị trí i** chứa **tổng** của **tất cả phần tử từ đầu mảng đến vị trí i.**

**Công thức:**  
F\[x\] = f\[x\] + F\[x − 1\]  
Sum\[a : b\] = F\[b\] − F\[a − 1\]

```python
def build_prefix_sum(data):
    """Xây dựng mảng tổng tiền tố"""
    prefix_sum = [0] * len(data)
    prefix_sum[0] = data[0]
    
    for i in range(1, len(data)):
        prefix_sum[i] = data[i] + prefix_sum[i-1]
    
    return prefix_sum

def range_sum(prefix_sum, left, right):
    """Tính tổng trong đoạn [left, right] với O(1)"""
    if left == 0:
        return prefix_sum[right]
    return prefix_sum[right] - prefix_sum[left-1]


original_data = [1, 8, 5, 7, 3, 5, 8, 3]
prefix_array = build_prefix_sum(original_data)
# prefix_array = [1, 9, 14, 21, 24, 29, 37, 40]

# Tính tổng từ index 3 đến 6: O(1)
result = range_sum(prefix_array, 3, 6)  # Output: 23
```

**Ứng dụng thực tế:**

* **Computer Vision**: Integral Image trong object detection
    
* **Competitive Programming**: Giải quyết range sum queries
    
* **Database Optimization**: Tối ưu hóa aggregate queries
    
* **Signal Processing**: Tính convolution và filtering
    

### **Mutable vs Immutable Operations**

```python
# Immutable - Tạo list mới
def square_immutable(data):
    result = []
    for value in data:
        result.append(value * value)
    return result

# Mutable - Thay đổi list gốc
def square_mutable(data):
    for i in range(len(data)):
        data[i] = data[i] * data[i]

data = [6, 5, 7, 1, 9, 2]
new_data = square_immutable(data)  # data không đổi
square_mutable(data)               # data bị thay đổi
```

## **VI. Kết luận và Hướng phát triển**

### **Tóm tắt Kiến thức**

List là cấu trúc dữ liệu fundamental trong Python với nhiều tính năng mạnh [m](https://www.w3schools.com/python/python_lists.asp)[ẽ](https://www.digitalocean.com/community/tutorials/understanding-lists-in-python-3). Từ những thao tác cơ bản như [i](https://www.digitalocean.com/community/tutorials/understanding-lists-in-python-3)ndexing và slicin[g](https://www.w3schools.com/python/python_lists.asp) đến các thuật toán phức tạp như sorting và searching, List đóng vai trò then chốt trong hầu hết các ứng dụng Pyth[o](https://www.topcoder.com/thrive/articles/python-data-structures-list-and-tuples)n. Hiểu rõ về độ phức tạp thuật [t](https://www.topcoder.com/thrive/articles/python-data-structures-list-and-tuples)oán giúp chúng ta [l](https://www.topcoder.com/thrive/articles/python-data-structures-list-and-tuples)ựa chọn phương pháp tối ưu cho từng bài toán cụ thể.

### **Hướng Phát triển**

Để nâng cao kỹ năng làm việc với List, chúng ta nên:

1. **Thực hành thuật toán**: Implement các sorting algorithms khác nhau
    
2. **Tối ưu hóa hiệu suất**: Sử dụng NumPy cho các phép toán ma trận phức tạp
    
3. **Ứng dụng thực tế**: Áp dụng vào computer vision và data science
    
4. **Học advanced techniques**: Dynamic programming với prefix sum
    

**Nguồn tham khảo (tài liệu gốc):** [**Data Structure Delving into List**](https://aivnlearning.edu.vn/api/files/68317562519c0e157fb51480/Documents%2F2025-5%2FM01W02%20-%20Delving%20into%20List%2FM01W02_DataStructure_List_v4.pdf)