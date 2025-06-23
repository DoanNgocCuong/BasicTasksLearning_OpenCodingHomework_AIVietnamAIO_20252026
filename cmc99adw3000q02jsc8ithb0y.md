---
title: "Linux - Docker - Github [Nhật ký học và làm]"
datePublished: Mon Jun 23 2025 15:33:14 GMT+0000 (Coordinated Universal Time)
cuid: cmc99adw3000q02jsc8ithb0y
slug: linux-docker-github-nhat-ky-hoc-va-lam
tags: linux, engineering, mlops

---

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750663929277/9e230d34-f088-4af7-840a-00d7a1e1125d.png align="center")

Có nhiều bản phân phối Linux phổ biến. Một trong số hay sử dụng đó là: Ubuntu

## **2.1 Hướng dẫn cài đặt Ubuntu**

* Hướng dẫn Dual Boot Ubuntu và Windows (cài đặt song song Ubuntu và Windows trên cùng một máy tính)
    
    * [**Dual Boot Ubuntu**](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) (Recommended)
        
* Sử dụng Ubuntu trên Windows với WSL2 (không khuyến khích dùng)
    
    * [**How to install Linux on Windows with WSL**](https://learn.microsoft.com/en-us/windows/wsl/install)
        

> Tại sao Dual Boot Ubuntu được recommend hơn WSL2 (thay vì WSL2 rất tiện trong các IDEs VSCode, Cursor, ..)
> 
> * **Không truy cập trực tiếp phần cứng:**  
>     Ví dụ: Khi bạn muốn chạy các mô hình AI/Deep Learning sử dụng GPU (như TensorFlow với CUDA hoặc PyTorch GPU), WSL2 chỉ mới hỗ trợ một phần GPU với Windows 11 và driver đặc biệt, nhưng không đầy đủ và thường không ổn định. Ngoài ra, nếu bạn cần lập trình nhúng hoặc debug thiết bị ngoại vi qua cổng USB (ví dụ: nạp firmware cho Arduino, Raspberry Pi), WSL2 không cho phép truy cập trực tiếp đến các thiết bị này.
>     
> * **Không tương thích hoàn toàn phần mềm Linux:**  
>     Ví dụ: Các phần mềm giao diện đồ họa như GIMP, Blender, hoặc IDE như Eclipse trên Linux không chạy mượt trên WSL2, hoặc cần cấu hình phức tạp để hiển thị giao diện. Các dịch vụ hệ thống như NetworkManager, systemd, hoặc các phần mềm VPN nâng cao thường không hoạt động hoặc không thể cài đặt trên WSL2.
>     
> * **Thiếu trải nghiệm Linux thực sự:**  
>     Ví dụ: Bạn không thể thao tác với quá trình khởi động (bootloader như GRUB), không làm việc với phân vùng ổ cứng một cách trực tiếp, hoặc đơn giản như khi shutdown, restart hệ thống thì chỉ dừng lại ở mức tắt máy ảo của WSL2 chứ không mô phỏng đúng quy trình của một hệ điều hành Linux thực sự. Điều này khiến việc học quản trị hệ thống bị giới hạn và không sát với thực tế.
>     

> Khi đi làm, mình thậm chí còn không biết cả Docker, Github, Ubutu  
> Nhưng qua thời gian nhảy vào các bài toán thực: Không biết cũng phải deploy → dần dần Docker, Github, Unbuntu của mình tăng trưởng.  
> \- Ban đầu khi cần deploy cần gửi sources cho đồng đội nhờ → Sau dần được vào trong server Linux của công ty!

## 2.2 Các lệnh cơ bản

> Nhiều bạn hỏi có cần nhớ hết các lệnh không? Câu trả lời là: không, chỉ cần biết nó có và biết thuật ngữ để khi cần xài thì AI chat ra luôn.