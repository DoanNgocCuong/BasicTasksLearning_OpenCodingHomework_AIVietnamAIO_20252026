---
title: "M01W03T5 - Database - SQL (3)"
datePublished: Tue Jun 24 2025 11:05:02 GMT+0000 (Coordinated Universal Time)
cuid: cmcaf5bt7000a02lg5s2u5ohi
slug: m01w03t5-database-sql-3

---

# **I. SQL JOIN – Kết Hợp Dữ Liệu Từ Nhiều Bảng**

## 1\. INNER JOIN

**Bản chất:**  
INNER JOIN chỉ trả về những dòng có giá trị khớp ở cả hai bảng dựa trên điều kiện JOIN. Nếu không khớp, dòng đó bị loại bỏ khỏi kết quả.

**Cú pháp:**

```sql
sqlExplainSELECT ...
FROM A
INNER JOIN B
ON A.key = B.key;
```

**Ví dụ thực tế:**  
Giả sử bạn có hai bảng: `orders` và `customers`.  
Mục tiêu: Lấy order\_id, first\_name, last\_name của khách hàng đã đặt hàng.

```sql
sqlSELECT order_id, first_name, last_name
FROM orders o
INNER JOIN customers c ON o.customer_id = c.customer_id;
```

**Giải thích:**

* Chỉ những khách hàng có đơn hàng mới xuất hiện trong kết quả.
    
* Nếu một khách hàng chưa từng đặt hàng, họ sẽ không xuất hiện.
    

**Kết quả minh họa:**

| **order\_id** | **first\_name** | **last\_name** |
| --- | --- | --- |
| 5 | Clemmie | Betchley |
| 6 | Elka | Twiddell |
| ... | ... | ... |

## 2\. LEFT JOIN (LEFT OUTER JOIN)

**Bản chất:**  
LEFT JOIN trả về tất cả dòng từ bảng bên trái (A), và các dòng khớp từ bảng bên phải (B). Nếu không khớp, các cột của B sẽ là NULL.

**Cú pháp:**

```sql
sqlSELECT ...
FROM A
LEFT JOIN B
ON A.key = B.key;
```

**Ví dụ thực tế:**  
Lấy danh sách tất cả khách hàng cùng order\_id (nếu có):

```sql
sqlSELECT c.customer_id, c.first_name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
ORDER BY c.customer_id;
```

**Giải thích:**

* Tất cả khách hàng đều xuất hiện, kể cả người chưa từng đặt hàng (order\_id sẽ là NULL).
    

**Kết quả minh họa:**

| **customer\_id** | **first\_name** | **order\_id** |
| --- | --- | --- |
| 1 | Babara | NULL |
| 2 | Ines | 4 |
| ... | ... | ... |

## 3\. RIGHT JOIN (RIGHT OUTER JOIN)

**Bản chất:**  
RIGHT JOIN trả về tất cả dòng từ bảng bên phải (B), và các dòng khớp từ bảng bên trái (A). Nếu không khớp, các cột của A sẽ là NULL.

**Cú pháp:**

```sql
sqlSELECT ...
FROM A
RIGHT JOIN B
ON A.key = B.key;
```

**Ví dụ thực tế:**  
Lấy danh sách tất cả đơn hàng cùng thông tin khách hàng (nếu có):

```sql
sqlSELECT c.customer_id, c.first_name, o.order_id
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id
ORDER BY c.customer_id;
```

**Giải thích:**

* Tất cả đơn hàng đều xuất hiện, kể cả đơn hàng không có khách hàng (cột khách hàng sẽ là NULL).
    

**Kết quả minh họa:**

| **customer\_id** | **first\_name** | **order\_id** |
| --- | --- | --- |
| 2 | Ines | 4 |
| NULL | NULL | 11 |
| ... | ... | ... |

## 4\. FULL OUTER JOIN

**Bản chất:**  
FULL OUTER JOIN trả về tất cả dòng từ cả hai bảng, kết hợp các dòng khớp và giữ lại các dòng không khớp ở cả hai bên (các cột bên không có sẽ là NULL).

**Cú pháp:**  
(MySQL không hỗ trợ trực tiếp FULL OUTER JOIN, nhưng bạn có thể mô phỏng bằng UNION của LEFT JOIN và RIGHT JOIN.)

```sql
sqlSELECT ...
FROM A
LEFT JOIN B ON A.key = B.key
UNION
SELECT ...
FROM A
RIGHT JOIN B ON A.key = B.key;
```

**Ví dụ thực tế:**  
Lấy tất cả khách hàng và tất cả đơn hàng, kể cả khách hàng chưa từng đặt hàng và đơn hàng không có khách hàng:

```sql
sqlSELECT c.customer_id, c.first_name, o.order_id
FROM customers c
FULL OUTER JOIN orders o ON c.customer_id = o.customer_id;
```

**Giải thích:**

* Kết quả gồm mọi khách hàng và mọi đơn hàng. Nếu không có đối tượng khớp, phần còn lại sẽ là NULL.
    

**Kết quả minh họa:**

| **customer\_id** | **first\_name** | **order\_id** |
| --- | --- | --- |
| 1 | Babara | NULL |
| NULL | NULL | 13 |
| ... | ... | ... |

## 5\. SELF JOIN

**Bản chất:**  
SELF JOIN là kỹ thuật JOIN một bảng với chính nó, thường dùng để truy vấn các mối quan hệ phân cấp (nhân viên – quản lý, sản phẩm cha – con...).

**Cú pháp:**

```sql
sqlSELECT a.column, b.column
FROM table a
JOIN table b ON a.related_id = b.id;
```

**Ví dụ thực tế:**  
Lấy tên nhân viên và tên quản lý của họ:

```sql
sqlSELECT 
    e.employee_id, 
    e.first_name, 
    e.last_name,
    m.employee_id as manager_id,
    m.first_name,
    m.last_name
FROM employees e
JOIN employees m ON e.reports_to = m.employee_id;
```

**Giải thích:**

* Bảng `employees` được tham chiếu hai lần với hai alias: e (nhân viên), m (quản lý).
    
* Dùng JOIN để tìm tên quản lý tương ứng với từng nhân viên.
    

**Kết quả minh họa:**

| **employee\_id** | **first\_name** | **last\_name** | **manager\_id** | **manager\_first** | **manager\_last** |
| --- | --- | --- | --- | --- | --- |
| 33391 | D'arcy | Nortunen | 37270 | Yovonnda | Magrannell |
| ... | ... | ... | ... | ... | ... |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750617888597/b6339cd8-5d98-45cd-adc4-1495627aaf69.png align="center")

## 6\. JOIN nhiều bảng (Multiple JOIN)

**Bản chất:**  
Bạn có thể JOIN nhiều bảng liên tiếp để lấy dữ liệu từ nhiều nguồn cùng lúc.

**Cú pháp:**

```sql
sqlSELECT ...
FROM A
JOIN B ON ...
JOIN C ON ...
```

**Ví dụ thực tế:**  
Lấy order\_id, order\_date, tên khách hàng, trạng thái đơn hàng:

```sql
sqlSELECT 
    o.order_id, 
    o.order_date, 
    c.last_name,
    c.first_name,
    s.name AS status
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_statuses s ON o.status = s.order_status_id;
```

**Kết quả minh họa:**

| **order\_id** | **order\_date** | **last\_name** | **first\_name** | **status** |
| --- | --- | --- | --- | --- |
| 5 | 2017-08-25 | Betchley | Clemmie | Shipped |
| ... | ... | ... | ... | ... |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750617762548/aca8fa0a-409e-48ec-89ce-970b97e2a8fb.png align="center")

## 7\. COMPOUND JOIN CONDITION & USING CLAUSE

**Bản chất:**  
Khi JOIN dựa trên nhiều cột (composite key), bạn cần liệt kê tất cả các cột trong điều kiện JOIN. Nếu các cột cùng tên, có thể dùng USING để viết gọn.

**Cú pháp:**

```sql
sqlSELECT *
FROM order_items o
JOIN order_item_notes n
  ON o.order_id = n.order_id
 AND o.product_id = n.product_id;
-- Hoặc
SELECT *
FROM order_items o
JOIN order_item_notes n
USING (order_id, product_id);
```

## 8\. IMPLICIT JOIN SYNTAX (KHÔNG KHUYẾN KHÍCH)

**Bản chất:**  
Có thể viết JOIN theo kiểu cũ, nhưng không nên dùng vì dễ nhầm lẫn giữa điều kiện JOIN và điều kiện lọc.

**Cú pháp:**

```sql
sqlSELECT *
FROM orders o, customers c
WHERE o.customer_id = c.customer_id;
```

**Nên dùng cú pháp JOIN tường minh để code rõ ràng, dễ bảo trì.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750617888217/5ab77143-cf3c-489f-8c61-fa0a2330b3e0.png align="center")

# **II. Common Table Expression (CTE**[**)**](https://datapot.vn/all-types-of-joins-in-sql-queries/) **– Biểu Thức Bảng Chung**

**Khá**[**i**](https://neon.tech/postgresql/postgresql-tutorial/postgresql-full-outer-join) **niệm:**  
CTE là một tập kết quả tạm thời, đặy tên, dùng trong phạm vi một truy vấn duy nhất. Dùng CTE giúp truy vấn phức tạp trở nên dễ đọc, dễ bảo trì hơn, và có thể tái sử dụng trong cùng truy vấn.

**Cú pháp:**

```sql
sqlWITH cte_name AS (
    SELECT ...
    FROM ...
    WHERE ...
)
SELECT ...
FROM cte_name
JOIN ...
```

**Ví dụ:**  
Tìm khách hàng có tổng hóa đơn lớn nhất:

```sql
sqlWITH invoice_amount AS (
    SELECT client_id, SUM(invoice_total) AS invoice_amount
    FROM invoices
    GROUP BY client_id
    ORDER BY SUM(invoice_total) DESC
    LIMIT 1
)
SELECT c.client_id, c.name, i.invoice_amount
FROM clients c JOIN invoice_amount i USING (client_id);
```

**CTE đệ quy:**  
Dùng để xử lý dữ liệu cây/phân cấp (như tìm toàn bộ cấp dưới của một quản lý):

```sql
sqlWITH RECURSIVE Subordinates AS (
    SELECT employee_id, employee_name, manager_id
    FROM employees
    WHERE employee_name = 'Alice (CEO)'
    UNION ALL
    SELECT e.employee_id, e.employee_name, e.manager_id
    FROM employees e
    INNER JOIN Subordinates s ON e.manager_id = s.employee_id
)
SELECT * FROM Subordinates;
```

**Lưu ý:**

* CTE chỉ tồn tại trong phạm vi câu lệnh SQL đang thực thi.
    
* Có thể khai báo nhiều CTE cùng lúc, phân tách bằng dấu phẩy.
    

# **III.**Subquery – Truy vấn lồng nhau

**Khái niệm:**  
Subquery là truy vấn lồng bên trong một truy vấn khác, có thể xuất hiện ở SELECT, WHERE, FROM.

## Các loại subquery:

* **Subquery trong SELECT:** Tính toán động cho từng dòng.
    
* **Subquery trong WHERE:** Lọc dữ liệu theo điều kiện động.
    
* **Subquery trong FROM:** Tạo bảng tạm thời để JOIN hoặc truy vấn tiếp.
    

## Ví dụ subquery trong SELECT:

Lấy tổng hóa đơn của từng khách hàng:

```sql
sqlSELECT client_id,
       name,
       (SELECT SUM(invoice_total)
        FROM invoices
        WHERE c.client_id = client_id) AS invoice_amount
FROM clients c
ORDER BY invoice_amount DESC
LIMIT 1;
```

## Ví dụ subquery trong WHERE:

Lấy nhân viên có lương thấp nhất:

```sql
sqlSELECT employee_name, salary
FROM employees
WHERE salary = (SELECT MIN(salary) FROM employees);
```

**Lưu ý:**

* Subquery có thể trả về một giá trị (scalar), một dòng, hoặc một bảng.
    
* Subquery phức tạp có thể ảnh hưởng hiệu năng, nên cân nhắc dùng CTE hoặc temp table nếu cần tái sử dụng nhiều lần.
    

# IV. Temp Table – Bảng Tạm

**Khái niệm:**  
Bảng tạm là bảng lưu trữ dữ liệu tạm thời trong phiên làm việc, dùng để lưu kết quả trung gian, giảm lặp lại tính toán, tối ưu hiệu năng.

## Cú pháp tạo bảng tạm:

```sql
sqlCREATE TEMPORARY TABLE temp_invoice (
    client_id INT,
    invoice_sum DECIMAL(10,2),
    invoice_avg DECIMAL(10,2)
);
```

## Chèn dữ liệu vào bảng tạm:

```sql
sqlINSERT INTO temp_invoice
SELECT client_id, SUM(invoice_total), AVG(invoice_total)
FROM invoices
GROUP BY client_id;
```

## Sử dụng bảng tạm:

```sql
sqlSELECT * FROM temp_invoice;
```

**Lưu ý:**

* Bảng tạm chỉ tồn tại trong phiên hiện tại, tự động xóa khi phiên kết thúc.
    
* Có thể dùng bảng tạm để giảm tải tính toán lặp lại khi truy vấn phức tạp.
    

# V. Stored Procedure – Thủ Tục Lưu Trữ

**Khái niệm:**  
Stored Procedure là tập lệnh SQL được lưu trữ trong database, có thể gọi lại nhiều lần, tự động hóa các thao tác phức tạp hoặc lặp đi lặp lại.

## Cú pháp tạo procedure:

```sql
sqlDELIMITER //
CREATE PROCEDURE create_temp_invoice()
BEGIN
    DROP TABLE IF EXISTS temp_invoice;
    CREATE TEMPORARY TABLE temp_invoice (
        client_id INT,
        invoice_sum DECIMAL(10,2),
        invoice_avg DECIMAL(10,2)
    );
    INSERT INTO temp_invoice
    SELECT client_id, SUM(invoice_total), AVG(invoice_total)
    FROM invoices
    GROUP BY client_id;
END //
DELIMITER ;
```

## Gọi procedure:

```sql
sqlCALL create_temp_invoice();
```

## Procedure với tham số:

Có thể truyền tham số để tạo procedure linh hoạt hơn:

```sql
sqlCREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;
```

**Lưu ý:**

* Procedure tồn tại lâu dài trong database, không bị xóa khi đóng phiên.
    
* Hỗ trợ truyền tham số đầu vào, đầu ra.
    

# VI. Trigger – Kích Hoạt Tự Động

**Khái niệm:**  
Trigger là tập lệnh SQL tự động thực thi khi có sự kiện INSERT, UPDATE, DELETE trên một bảng.

## Ví dụ trigger ghi log khi thêm nhân viên mới:

```sql
sqlCREATE TRIGGER hire_log AFTER INSERT ON employees
FOR EACH ROW
INSERT INTO hiring VALUES (NEW.id, CURRENT_TIME());
```

## Trigger ghi nhận thay đổi tên nhân viên:

```sql
sqlCREATE TRIGGER name_change_trigger
AFTER UPDATE ON employees
FOR EACH ROW
INSERT INTO name_changes (emp_id, old_name, new_name)
VALUES (NEW.id, CONCAT(OLD.first_name, ' ', OLD.last_name), CONCAT(NEW.first_name, ' ', NEW.last_name));
```

## Trigger kiểm tra dữ liệu đầu vào (chuyển tên thành chữ hoa):

```sql
sqlCREATE TRIGGER upper_name_i
BEFORE INSERT ON employees
FOR EACH ROW
SET NEW.first_name = UPPER(NEW.first_name),
    NEW.last_name = UPPER(NEW.last_name);
```

**Lưu ý:**

* Trigger giúp đảm bảo tính toàn vẹn dữ liệu, tự động hóa nghiệp vụ.
    
* Lạm dụng trigger có thể gây khó debug, nên dùng hợp lý.
    

# VII. RECURSIVE IN SQL

RECURSIVE CTE (Common Table Expression đệ quy) là một kỹ thuật mạnh mẽ trong SQL để xử lý dữ liệu phân cấp (cây, tổ chức, phả hệ, v.v.). Điểm đặc biệt là CTE có thể tự tham chiếu chính nó, lặp lại nhiều lần cho đến khi không còn dữ liệu mới để truy xuất.

## Cấu trúc tổng quát:

```sql
sqlWITH RECURSIVE cte_name AS (
    -- Anchor member: phần neo, truy vấn cơ sở, trả về tập dữ liệu đầu tiên
    SELECT ... FROM ... WHERE ...
    UNION ALL
    -- Recursive member: phần đệ quy, truy vấn tham chiếu lại chính CTE
    SELECT ... FROM ... JOIN cte_name ON ...
)
SELECT * FROM cte_name;
```

* Anchor member: Truy vấn cơ sở, trả về kết quả ban đầu (ví dụ: node gốc của cây).
    
* Recursive member: Truy vấn tham chiếu lại chính CTE, mở rộng kết quả dựa trên tập trước đó.
    
* Hai phần này nối với nhau bằng UNION ALL.
    
* Quá trình lặp sẽ dừng khi truy vấn đệ quy không trả về thêm dòng nào mới.
    

## 2\. Ví dụ thực tế trên slide: Truy vấn cây quản lý nhân sự

Giả sử có bảng employees:

| **employee\_id** | **employee\_name** | **manager\_id** |
| --- | --- | --- |
| 1 | Alice (CEO) | NULL |
| 2 | Bob | 1 |
| 3 | Charlie | NULL |
| 4 | David | 2 |
| 5 | Eve | 2 |
| 6 | Frank | 3 |

**Yêu cầu:** Lấy toàn bộ cấp dưới của Alice (CEO).

## Câu lệnh RECURSIVE CTE:

```sql
sqlWITH RECURSIVE Subordinates AS (
    -- Anchor member: Lấy thông tin của Alice (CEO)
    SELECT employee_id, employee_name, manager_id
    FROM employees
    WHERE employee_name = 'Alice (CEO)'
    UNION ALL
    -- Recursive member: Lấy nhân viên mà manager_id trùng với employee_id của cấp trên vừa tìm được
    SELECT e.employee_id, e.employee_name, e.manager_id
    FROM employees e
    INNER JOIN Subordinates s ON e.manager_id = s.employee_id
)
SELECT * FROM Subordinates;
```

**Kết quả trả về:**

* Lần 1 (Anchor): Alice (CEO)
    
* Lần 2 (Đệ quy): Bob (cấp dưới trực tiếp của Alice)
    
* Lần 3 (Đệ quy): David, Eve (cấp dưới của Bob)
    
* Lần 4: Không còn ai có manager\_id là 4 hoặc 5 ⇒ dừng lặp
    

## 3\. Phân tích từng bước lặp (theo slide)

**Lần lặp 1 (Anchor Member):**

```sql
sqlSELECT employee_id, employee_name, manager_id
FROM employees
WHERE employee_name = 'Alice (CEO)';
```

Kết quả: (1, 'Alice (CEO)', NULL)

**Lần lặp 2 (Recursive Member):**

```sql
sqlSELECT e.employee_id, e.employee_name, e.manager_id
FROM employees e
INNER JOIN Subordinates s ON e.manager_id = s.employee_id;
```

Kết quả: (2, 'Bob', 1)

**Lần lặp 3:**

* Dựa trên kết quả trước, tìm ai có manager\_id = 2 (Bob): (4, 'David', 2), (5, 'Eve', 2)
    

**Lần lặp 4:**

* Không còn ai có manager\_id là 4 hoặc 5 ⇒ dừng.
    

**Tổng hợp kết quả cuối cùng:**

| **employee\_id** | **employee\_name** | **manager\_id** |
| --- | --- | --- |
| 1 | Alice (CEO) | NULL |
| 2 | Bob | 1 |
| 4 | David | 2 |
| 5 | Eve | 2 |

## 4\. Một số biến thể và ứng dụng

* Truy vấn toàn bộ cây tổ chức từ node bất kỳ:  
    Chỉ cần đổi điều kiện WHERE ở anchor member.
    
* Tìm tất cả cấp trên (ancestor) của một nhân viên:  
    Đổi chiều JOIN trong recursive member.
    
* Tìm đường đi, phân tích phả hệ, quản lý sản phẩm lắp ráp (BOM), duyệt thư mục...
    

## 5\. Lưu ý khi dùng RECURSIVE CTE

* Luôn có điều kiện dừng (termination condition) để tránh vòng lặp vô hạn.
    
* Có thể giới hạn độ sâu đệ quy bằng tham số hệ thống (ví dụ: MAXRECURSION trong SQL Server).
    
* Hiệu năng giảm khi dữ liệu rất lớn hoặc cây phân cấp sâu.