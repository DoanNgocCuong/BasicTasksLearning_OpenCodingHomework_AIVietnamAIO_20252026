---
title: "Linux - Docker - Github [Nhật ký học và làm]"
datePublished: Mon Jun 23 2025 15:33:14 GMT+0000 (Coordinated Universal Time)
cuid: cmc99adw3000q02jsc8ithb0y
slug: linux-docker-github-nhat-ky-hoc-va-lam
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1750695970891/a0ff5da1-79dd-41eb-9b75-99fb3d6125bb.png
tags: linux, engineering, mlops

---

Resources:  
1\. AIO: [AI VIET NAM](https://aivnlearning.edu.vn/)  
2\. FSDS: [https://fullstackdatascience.com/](https://fullstackdatascience.com/)  

> Đôi điều chú ý trong việc học:
> 
> 1. Begin with the end X3-X10 in Mind. The end with the number?  
>     Mục đích học tập phần này?
>     
> 2. Muốn đi nhanh: Mentor + Dự án thật + Dạy lại + Networking.
>     
> 3. The one thing: Tập trung 1 thứ và chỉ học những thứ bản thân thực sự dùng.
>     

# 1\. Tổng quan về Unix/Linux

# 2\. Các bản phân phối Linux phổ biến

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750694627832/9a7d9c34-e9c3-48fe-b97c-957cafcb412a.png align="center")

Có nhiều bản phân phối Linux phổ biến. Một trong số hay sử dụng nhất đó là: Ubuntu

## **2.1 Hướng dẫn cài đặt Ubuntu**

* Hướng dẫn Dual Boot Ubuntu và Windows (cài đặt song song Ubuntu và Windows trên cùng một máy tính)
    
    * [**Dual Boot Ubuntu**](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) (Recommended)
        
* Sử dụng Ubuntu trên Windows với WSL2 (không khuyến khích dùng)
    
    * [**How to install Linux on Windows with WSL**](https://learn.microsoft.com/en-us/windows/wsl/install)
        

> Tại sao Dual Boot Ubuntu được recommend hơn WSL2 (thay vì WSL2 rất tiện trong các IDEs VSCode, Cursor, ..)
> 
> * **<mark>Không truy cập trực tiếp phần cứng:</mark>**  
>     Ví dụ: Khi bạn muốn chạy các mô hình AI/Deep Learning sử dụng GPU (như TensorFlow với CUDA hoặc PyTorch GPU), WSL2 chỉ mới hỗ trợ một phần GPU với Windows 11 và driver đặc biệt, nhưng không đầy đủ và thường không ổn định. Ngoài ra, nếu bạn cần lập trình nhúng hoặc debug thiết bị ngoại vi qua cổng USB (ví dụ: nạp firmware cho Arduino, Raspberry Pi), WSL2 không cho phép truy cập trực tiếp đến các thiết bị này.
>     
> * **<mark>Không tương thích hoàn toàn phần mềm Linux:</mark>**  
>     Ví dụ: Các phần mềm giao diện đồ họa như GIMP, Blender, hoặc IDE như Eclipse trên Linux không chạy mượt trên WSL2, hoặc cần cấu hình phức tạp để hiển thị giao diện. Các dịch vụ hệ thống như NetworkManager, systemd, hoặc các phần mềm VPN nâng cao thường không hoạt động hoặc không thể cài đặt trên WSL2.
>     
> * **<mark>Thiếu trải nghiệm Linux thực sự:</mark>**  
>     Ví dụ: Bạn không thể thao tác với quá trình khởi động (bootloader như GRUB), không làm việc với phân vùng ổ cứng một cách trực tiếp, hoặc đơn giản như khi shutdown, restart hệ thống thì chỉ dừng lại ở mức tắt máy ảo của WSL2 chứ không mô phỏng đúng quy trình của một hệ điều hành Linux thực sự. Điều này khiến việc học quản trị hệ thống bị giới hạn và không sát với thực tế.
>     

> Thời điểm bắt đầu đi thực tập 27/06/2024 (tròn 1 năm lúc mình viết bài này) và mình thậm chí còn không biết cả Docker, Github, Ubutu. Nhờ vào việc nhảy vào các bài toán thực: Không biết cũng phải deploy → dần dần Docker, Github, Unbuntu của mình tăng trưởng.  
> \- Ban đầu khi cần deploy cần gửi sources cho đồng đội nhờ → Sau dần được vào trong server Linux của công ty!

## 2.2 Linux Directory Structure

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750693417987/98c3e9e2-1a71-43ff-8a97-5f4d33e53301.png align="center")

* Đối với người dùng thông thường: **/home** là quan trọng nhất vì chứa tất cả dữ liệu cá nhân.
    
* Đối với quản trị hệ thống: **/etc** là quan trọng nhất vì chứa toàn bộ cấu hình hệ thống.
    

## 2.3 Các lệnh cơ bản

> Nhiều bạn hỏi có cần nhớ hết các lệnh không? Câu trả lời là: không,  
> Tuy nhiên chỉ có khoảng 20% lệnh phổ biến, làm nhiều sẽ tự nhiên nhớ.  
> 80% Các lệnh còn lại chỉ cần biết nó có và biết thuật ngữ để khi cần xài thì AI search ra được.

Thông thường trong công việc, chúng ta sẽ thường SSH vào server của công ty qua VSCode/Cursor, và thao tác rất đơn giản với các file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750694116879/4df4553f-5e68-490f-9617-334792181fcf.png align="center")

---

### 2.3.1 **Lệnh điều hướng và quản lý thư mục**

| Lệnh | Mô tả |
| --- | --- |
| `pwd` | Hiển thị đường dẫn thư mục hiện tại |
| `cd <dir>` | Di chuyển vào thư mục `<dir>` |
| `cd ..` | Lùi về thư mục cha |
| `cd ~` | Về thư mục home của user |
| `ls` | Liệt kê nội dung thư mục |
| `mkdir <name>` | Tạo thư mục mới |

### **2.3.2 Docker Compose**

| Lệnh | Mô tả |
| --- | --- |
| `docker compose up --build -d` | Build lại và chạy container ở chế độ nền |
| `docker compose logs` | Hiển thị log của các service |
| `docker compose down` | Dừng và xoá containers, networks |
| `docker compose ps` | Kiểm tra trạng thái container |

### **2.3.3. Các lệnh nâng cao hữu dụng**

Trong quá trình làm việc, mình rất hay gặp các task như sau:

* Cần chạy script Python ngầm trên server để có thể **đóng terminal hoặc tắt máy** mà tiến trình vẫn tiếp tục (ví dụ: chạy xong rồi về nhà 😄).
    
* Cần **chia sẻ folder ảnh hoặc web HTML demo** cho người khác qua trình duyệt mà không cần deploy phức tạp (chỉ cần mở local HTTP server là đủ).  
    (Thay vì phải loay hoay gửi ảnh ở Drive, hoặc loay hoay deploy web phức tạp thì HTML là 1 lựa chọn nhanh gọn)
    

| **Lệnh** | **Mô tả Use Case** |
| --- | --- |
| `nohup python3` [`script.py`](http://script.py) `> log.txt 2>&1 &` | Chạy [`script.py`](http://script.py) ở chế độ nền, log cả stdout và stderr vào `log.txt`. Terminal có thể đóng mà script vẫn chạy. |
| `nohup python3 -m http.server 3000 > web.log 2>&1 &` | Mở HTTP server trên port `3000` để người khác có thể truy cập folder ảnh hoặc HTML demo qua trình duyệt. |

\[TO BE CONTINUED\]

---

Linkedin: [https://www.linkedin.com/posts/doan-ngoc-cuong\_b%E1%BA%A5t-ng%E1%BB%9D-nh%E1%BA%ADn-ra-ch%C6%B0a-%C4%91%E1%BA%BFn-10-l%E1%BB%87nh-linux-activity-7342957359033368579-6lvT?utm\_source=social\_share\_send&utm\_medium=member\_desktop\_web&rcm=ACoAAC3wojwBYfkOk3q0b6y8Z\_UF\_N5ELvjQYVI](https://www.linkedin.com/posts/doan-ngoc-cuong_b%E1%BA%A5t-ng%E1%BB%9D-nh%E1%BA%ADn-ra-ch%C6%B0a-%C4%91%E1%BA%BFn-10-l%E1%BB%87nh-linux-activity-7342957359033368579-6lvT?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAC3wojwBYfkOk3q0b6y8Z_UF_N5ELvjQYVI)