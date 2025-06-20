---
title: "Understanding SQL for Beginners: Database Basics"
datePublished: Wed Jun 11 2025 11:59:36 GMT+0000 (Coordinated Universal Time)
cuid: cmbrwdeyl000w02jsfi2p254b
slug: understanding-sql-for-beginners-database-basics
tags: databases, sql, alo2025

---

Nguồn tham khảo: [2025-5/M01W01 - \[v2\] Database - SQL (1)/AIO2025\_SQL1\_v2](https://aivnlearning.edu.vn/api/files/68311fda519c0e157fb51460/Documents%2F2025-5%2FM01W01%20-%20%5Bv2%5D%20Database%20-%20SQL%20\(1\)%2FAIO2025_SQL1_v2.pdf)

## **1\. Giới thiệu về Cơ sở dữ liệu & SQL**

* **Cơ sở dữ liệu (Database)** là tập hợp dữ liệu được lưu trữ, tổ chức theo cấu trúc để dễ dàng truy cập, quản lý và xử lý.
    
* **DBMS (Database Management System)** là phần mềm cho phép người dùng tương tác với cơ sở dữ liệu (MySQL, SQL Server, Oracle...).
    
* **Mô hình quan hệ**: Dữ liệu được lưu trữ trong các bảng (table), mỗi bảng gồm các dòng (record/row) và cột (field/column).
    
* **Ví dụ thực tế:**
    
    | **CustomerID** | **Name** | **Address** |
    | --- | --- | --- |
    | 1 | Nguyen Van A | Tay Ninh |
    | 2 | Nguyen Van B | Can Tho |
    
    ## **2\. Hướng dẫn cài đặt MySQL**
    
    ## **Trên MacOS**
    
    * Truy cập [mysql.com](http://mysql.com) → DOWNLOADS → MySQL Community Server.
        
    * Mở file cài đặt, cấp quyền bảo mật nếu bị chặn.
        
    * Đặt mật khẩu cho user “root”.
        
    * Tải và cài đặt MySQL Workbench.
        
    
    ## **Trên Windows**
    
    * Tương tự MacOS, tải MySQL Community Server và MySQL Workbench.
        
    * Làm theo hướng dẫn cài đặt, đặt mật khẩu cho user “root”.
        
    
    ---
    
    ## **3\. Thiết kế & Tạo cơ sở dữ liệu đầu tiên**
    
    ## **Các bước cơ bản**
    
    1. Thiết kế lược đồ (schema) – xác định các bảng, trường, mối quan hệ.
        
    2. Tạo bảng (table) bằng lệnh `CREATE TABLE`.
        
    3. Chèn dữ liệu (INSERT).
        
    4. Truy vấn dữ liệu (SELECT).
        
    5. Cập nhật/xóa dữ liệu (UPDATE/DELETE).
        
    
    ## **Ví dụ: Thiết kế hệ thống bán hàng**
    
    * **Bảng Customers:** Lưu thông tin khách hàng.
        
    * **Bảng Products:** Lưu thông tin sản phẩm.
        
    * **Bảng Orders:** Lưu thông tin đơn hàng.
        
    * **Bảng OrderItems:** Lưu chi tiết từng sản phẩm trong đơn hàng.
        
    
    **Sơ đồ ERD:**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749451353737/3ab427b4-e63a-4b5a-921c-731e2f520a87.png align="center")
    
    .
    
    **SQL-AI Assistant**
    
    SQL-AI Assistant là công cụ hỗ trợ sinh câu lệnh SQL từ mô tả tự nhiên, giúp bạn tiết kiệm thời gian và giảm lỗi cú pháp:
    
    * Bạn chỉ cần nhập mô tả nghiệp vụ hoặc yêu cầu dữ liệu bằng tiếng Việt hoặc tiếng Anh, ví dụ:  
        “Tạo hệ thống bán hàng online với các bảng: khách hàng, sản phẩm, đơn hàng, chi tiết đơn hàng.”
        
    * AI Assistant (như ChatGPT, Copilot, hoặc các công cụ AI tích hợp trong nền tảng như Oracle APEX) sẽ:
        
        * Nhận diện các bảng, trường cần thiết dựa trên mô tả.
            
        * Sinh ra câu lệnh SQL tạo bảng hoặc truy vấn dữ liệu phù hợp.
            
    * Bạn có thể yêu cầu AI sinh các truy vấn phân tích dữ liệu, ví dụ: tổng doanh thu theo sản phẩm, danh sách khách hàng mua nhiều nhất, v.v.
        
    * Sau khi nhận được câu lệnh SQL từ AI, bạn kiểm tra lại và chạy trên MySQL Workbench hoặc môi trường tương ứng để lấy kết quả.
        
    
    **Ví dụ prompt:**  
    “Viết câu lệnh SQL tạo bảng customer, product, order, order\_detail cho hệ thống bán hàng online.”
    
    **Lợi ích:**
    
    * Tiết kiệm thời gian viết lệnh SQL.
        
    * Hỗ trợ cả người mới và người có kinh nghiệm khi muốn tối ưu hoặc kiểm tra cú pháp.
        
    * Có thể dùng để giải thích, sửa lỗi, hoặc cải thiện câu lệnh SQL hiện tại.
        

# Truy vấn dữ liệu với SQL (SQL Queries)

## 1\. **SELECT – Truy vấn dữ liệu cơ bản**

### **Lấy toàn bộ dữ liệu từ một bảng:**

* ```sql
          SELECT * FROM <schema>.<table>;
    ```
    
    Hoặc nếu đã chọn schema:
    
* ```sql
          USE sql_store;
          SELECT * FROM orders;
    ```
    
* Chọn một số cột cụ thể\*\*:\*\*
    
* ```sql
          SELECT first_name, last_name FROM customers;
    ```
    

## 2\. **Biến đổi và đặt tên cột trong truy vấn**

* **Tính toán trên cột:**
    
* ```sql
          SELECT points, points + 10, points / 10 FROM customers;
          SELECT points, points * 110 / 100 AS VAT FROM customers;
    ```
    
* **Đặt bí danh (alias) cho cột:**
    
* ```sql
          SELECT <column> AS <alias> FROM <table>;
    ```
    

## 3\. **Lấy giá trị duy nhất và xử lý dữ liệu**

* **Chỉ lấy giá trị duy nhất:**
    
    ```sql
    SELECT DISTINCT state FROM customers;
    ```
    
* **Tính toán giá mới cho sản phẩm:**
    
* ```sql
          SELECT name, unit_price, unit_price * 1.1 AS new_price FROM products;
    ```
    

## 4\. **Lọc dữ liệu với WHERE**

* **Lọc theo điều kiện:**
    
* ```sql
          SELECT * FROM customers WHERE points > 3000;
          SELECT * FROM customers WHERE state = 'VA';
          SELECT * FROM customers WHERE state != 'VA';
          SELECT * FROM orders WHERE order_date >= '2018-01-01';
    ```
    
* **Kết hợp điều kiện với AND, OR, NOT:Kết hợp điều kiện với AND, OR, NOT:**
    
* ```sql
          SELECT * FROM customers WHERE state = 'VA' AND points > 1000;
          SELECT * FROM customers WHERE state = 'VA' OR state = 'GA';
          SELECT * FROM customers WHERE NOT state = 'VA';
    ```
    
* **Tính toán trong điều kiện:**
    
* ```sql
          SELECT *, unit_price * quantity AS total_price
          FROM order_items
          WHERE order_id = 6 AND unit_price * quantity < 30;
    ```
    

## 5\. **IN và BETWEEN**

* **Lọc với nhiều giá trị (IN):**
    
* ```sql
          SELECT * FROM customers WHERE state IN ('VA', 'GA', 'FL');
    ```
    
* **Lọc trong khoảng (BETWEEN):**
    
* ```sql
          SELECT * FROM customers WHERE points BETWEEN 300 AND 2000;
    ```
    
* **Kết hợp IN và BETWEEN:**
    
* ```sql
          SELECT * FROM customers
          WHERE state IN ('VA', 'GA', 'FL') AND points BETWEEN 300 AND 2000;
    ```
    

## 6\. **Kiểm tra giá trị NULL, sắp xếp và giới hạn kết quả**

* **Kiểm tra dữ liệu NULL:**
    
* ```sql
          SELECT * FROM customers WHERE phone IS NULL;
          SELECT * FROM customers WHERE phone IS NOT NULL;
    ```
    
* **Sắp xếp kết quả:**
    
* ```sql
          SELECT * FROM customers ORDER BY points;
          SELECT * FROM customers WHERE points < 1000 ORDER BY points DESC;
    ```
    
* **Giới hạn số dòng trả về (LIMIT):**
    
* ```sql
          SELECT * FROM customers ORDER BY points DESC LIMIT 3;
          SELECT * FROM customers ORDER BY points DESC LIMIT 3, 4; 
          --(3 là số dòng bỏ qua, 4 là số dòng lấy tiếp theo)
    ```
    

## 7\. **LIKE và REGEXP – Tìm kiếm nâng cao**

* **LIKE – tìm kiếm theo mẫu:**
    
* ```sql
          SELECT * FROM customers WHERE last_name LIKE 'B%';         -- bắt đầu bằng B
          SELECT * FROM customers WHERE last_name LIKE '%B%';        -- chứa B
          SELECT * FROM customers WHERE last_name LIKE '_____y';     -- 6 ký tự, kết thúc bằng y
          SELECT * FROM customers WHERE address LIKE '%trail%' OR address LIKE '%avenue%'; -- chứa trail hoặc avenue
          SELECT * FROM customers WHERE phone LIKE '%9___';          -- kết thúc bằng 9 và còn 3 ký tự
    ```
    
* **REGEXP – tìm kiếm nâng cao với biểu thức chính quy:**
    
* ```sql
          SELECT * FROM customers WHERE first_name REGEXP 'ELKA|AMBUR';           -- tên là ELKA hoặc AMBUR
          SELECT * FROM customers WHERE last_name REGEXP 'EY$|ON$';               -- kết thúc bằng EY hoặc ON
          SELECT * FROM customers WHERE last_name REGEXP '^MY|SE';                -- bắt đầu bằng MY hoặc chứa SE
          SELECT * FROM customers WHERE last_name REGEXP 'B[RU]';                 -- chứa BR hoặc BU
    ```