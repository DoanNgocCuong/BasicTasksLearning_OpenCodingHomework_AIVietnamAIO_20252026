---
title: "SQL in Data Analysis 
(ERD & Database Normalization)"
datePublished: Mon Jun 16 2025 01:29:30 GMT+0000 (Coordinated Universal Time)
cuid: cmbyf2cys000102l5hp0ifqct
slug: sql-in-data-analysis-erd-and-database-normalization

---

## **1\. Giới thiệu về ERD (Entity Relationship Diagram)**

**Khái niệm**

ERD là sơ đồ trực quan hóa các thực thể (entity) trong hệ thống và mối quan hệ giữa chúng. Đây là công cụ nền tảng để thiết kế, mô hình hóa cơ sở dữ liệu quan hệ, giúp bạn hình dung cấu trúc logic trước khi xây dựng thực tế.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749985522315/0911b190-d0d4-4789-afd9-1a2d812407c5.png align="center")

## **2\. Các ký hiệu và thành phần cơ bản trong ERD**

**Nội dung:**

* **Thực thể (Entity):** Hình chữ nhật, đặt tên danh từ số ít.
    
* **Thuộc tính (Attribute):** Hình oval, nối với thực thể.
    
* **Khóa chính (Key Attribute):** Gạch chân tên thuộc tính.
    
* **Thuộc tính đa trị, tổng hợp, dẫn xuất:** Có ký hiệu riêng biệt.
    
* **Quan hệ (Relationship):** Hình thoi nối giữa các thực thể.
    
* **Bội số (Cardinality):** Chân quạ hoặc số (1, N, M).
    

## **Thực thể yếu(Weak Entity)**

Thực thể yếu là thực thể không thể xác định duy nhất chỉ bằng các thuộc tính của nó, mà phải kết hợp với khóa chính từ một thực thể khác (thực thể mạnh). Ví dụ điển hình là **Order Item** trong hệ thống bán hàng: một Order Item chỉ có ý nghĩa khi gắn với một Order cụ thể – nó phụ thuộc vào Order để tồn tại. Trong ERD, thực thể yếu thường được vẽ bằng hình chữ nhật viền đôi, và mối quan hệ xác định với thực thể mạnh cũng dùng đường viền đôi.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749986137542/51fb7852-5ff6-492c-8370-b893c71ed30b.png align="center")

## Thực thể liên kết (Associative Entity)

Thực thể liên kết dùng để biểu diễn mối quan hệ nhiều-nhiều giữa hai thực thể khác. Nó thường là bảng trung gian chứa khóa ngoại của hai thực thể liên quan, đồng thời có thể có thêm các thuộc tính riêng (ví dụ: số lượng, đơn giá trong Order Item). Trong ERD, thực thể liên kết cũng được vẽ như một thực thể bình thường.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749986177315/42e64fc3-db91-4789-8b54-b78d3e2a403d.png align="center")

## **Thuộc tính (Attribute) trong ERD**

Thuộc tính là đặc điểm mô tả cho thực thể, giúp nhận diện hoặc bổ sung thông tin cho từng thực thể. Trong ERD, thuộc tính được vẽ bằng hình oval nối với thực thể.  
Có nhiều loại thuộc tính, gồm:

* **Thuộc tính đơn (simple/single-valued):** Không chia nhỏ được, ví dụ: Age, Gender.
    
* **Thuộc tính tổng hợp (composite):** Có thể chia thành các thành phần nhỏ hơn, ví dụ: Address gồm street, city, zip.
    
* **Thuộc tính đa trị (multivalued):** Có thể có nhiều giá trị cho một thực thể, ví dụ: một nhân viên có nhiều số điện thoại.
    
* **Thuộc tính dẫn xuất (derived):** Được tính từ thuộc tính khác, ví dụ: Age tính từ Birthdate.
    

## **4\. Các kiểu quan hệ và ràng buộc tham gia**

## **Các kiểu quan hệ trong ERD**

* **Quan hệ 1-1 (One-to-One, 1:1):** Một thực thể ở bảng A chỉ liên kết với tối đa một thực thể ở bảng B và ngược lại. Ví dụ: mỗi người chỉ có một hộ chiếu, mỗi hộ chiếu chỉ cấp cho một người.
    
* **Quan hệ 1-N (One-to-Many, 1:N):** Một thực thể ở bảng A có thể liên kết với nhiều thực thể ở bảng B, nhưng mỗi thực thể ở bảng B chỉ thuộc về một thực thể ở bảng A. Ví dụ: một khách hàng có nhiều đơn hàng, nhưng mỗi đơn hàng chỉ thuộc về một khách hàng.
    
* **Quan hệ N-M (Many-to-Many, M:N):** Một thực thể ở bảng A có thể liên kết với nhiều thực thể ở bảng B và ngược lại. Ví dụ: một sinh viên học nhiều môn, một môn có nhiều sinh viên đăng ký. Quan hệ này thường được chuyển thành hai quan hệ 1-N thông qua bảng liên kết.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749986561679/0d9664a6-fb20-436b-bea7-b3b02f12ef24.png align="center")

## **Ràng buộc tham gia (Participation Constraints)**

* **Tham gia toàn phần (Total Participation):** Mọi thực thể trong một tập thực thể bắt buộc phải tham gia vào quan hệ. Trong ERD, thường ký hiệu bằng đường đôi nối giữa thực thể và quan hệ. Ví dụ: mỗi chương phải thuộc về một cuốn sách.
    
* **Tham gia một phần (Partial Participation**[**)**](https://www.exploredatabase.com/2018/04/define-partial-participation-in-er-diagram-model.html)[**:**](https://www.cse.cuhk.edu.hk/~taoyf/course/bmeg3120/notes/er.pdf) Chỉ một số thực thể trong tập thực thể tham gia vào quan hệ, không bắt buộc tất cả. Ký hiệu bằng một đường đơn nối giữa thực thể và quan hệ. Ví dụ: không phải khách hàng nào cũng có đơn hàng, nên khách hàng tham gia một phần vào quan hệ với đơn hàng.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749986854078/a0aac91c-5132-4475-b0bd-cc916301661c.png align="center")

## Crow’s Foot Notation

**Định nghĩa**

**Crow’s Foot Notation** là một phương pháp ký hiệu trực quan, phổ biến nhất dùng để mô hình hóa các mối quan hệ giữa các thực thể trong ERD. Ký hiệu này sử dụng các hình dạng đặc trưng như “chân quạ” (ba nhánh), vạch dọc và vòng tròn để thể hiện số lượng (cardinality) và tính bắt buộc (modality) của mối quan hệ.

* **Vạch dọc (|):** Thể hiện “một” (one).
    
* **Chân quạ (crow’s foot):** Thể hiện “nhiều” (many).
    
* **Vòng tròn (o):** Thể hiện “không” (zero, tùy chọn).
    

Kết hợp các ký hiệu này, bạn có thể đọc được quan hệ 1-1, 1-nhiều, nhiều-nhiều, bắt buộc hoặc tùy chọn giữa các thực thể. Ví dụ: Một khách hàng có thể có nhiều đơn hàng (1:N), nhưng mỗi đơn hàng chỉ thuộc về một khách hàng (N:1)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749987102373/83a1edcc-6d0e-466d-8f91-f92b02425390.png align="center")

## **Làm sao để vẽ ER Diagram**

1. **Xác định các thực thể (entities)**  
    Liệt kê tất cả các thực thể sẽ quản lý trong hệ thống (ví dụ: Customer, Product, Order). Vẽ mỗi thực thể bằng một hình chữ nhật và đặt tên rõ ràng.
    
2. **Xác định các mối quan hệ (relationships)**  
    Vẽ các đường nối giữa các thực thể để thể hiện quan hệ, có thể thêm hình thoi ở giữa để ghi chú tên quan hệ (theo Chen notation). Xác định kiểu quan hệ (1-1, 1-N, N-M) và ràng buộc tham gia.
    
3. **Thêm các thuộc tính (attributes)**  
    Vẽ các thuộc tính dưới dạng hình oval, nối với thực thể tương ứng. Đánh dấu thuộc tính khóa chính bằng gạch chân.
    
4. **Rà soát, sắp xếp lại sơ đồ**  
    Kiểm tra lại các thực thể, quan hệ, thuộc tính đã đầy đủ và hợp lý chưa. Sắp xếp sơ đồ cho dễ nhìn, logic.
    

## Một số công cụ vẽ ERD phổ biến

* **Lucidchart**  
    Công cụ online mạnh mẽ, hỗ trợ kéo thả, nhiều mẫu ERD, dễ cộng tác nhóm. Có bản miễn phí cho cá nhân và trả phí cho doanh nghiệp.
    
* **Draw.io (diagrams.net)**  
    Miễn phí hoàn toàn, chạy trên web hoặc cài offline, giao diện trực quan, tích hợp với Google Drive/OneDrive, phù hợp cho cả cá nhân lẫn nhóm.
    
* **dbdiagram.io**  
    Tạo ERD nhanh bằng cách nhập code, phù hợp cho developer, xuất file ảnh hoặc SQL, miễn phí bản cơ bản.
    
* **ERDPlus**  
    Web app đơn giản, miễn phí, hỗ trợ vẽ ERD, relational schema, star schema và xuất file PNG hoặc SQL.
    
* **QuickDBD**  
    Vẽ sơ đồ bằng cách nhập text, thao tác cực nhanh, miễn phí cho 1 diagram nhỏ, có bản trả phí mở rộng.
    
* **Visual Paradigm**  
    Công cụ chuyên nghiệp, nhiều template, hỗ trợ xuất ảnh không watermark, phù hợp cả cá nhân và doanh nghiệp.
    
* **Creately, Cacoo, Gliffy, SmartDraw, Canva, GitMind**  
    Các lựa chọn khác với giao diện kéo thả, nhiều mẫu đẹp, hỗ trợ làm việc nhóm và xuất file ở nhiều định dạng.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750000238348/1a1bd07d-1274-4834-ab29-209aeaa7b153.png align="center")

## Case Study: Thiết Kế ERD Cho Hệ Thống Bán Hàng

**1\. Xác định yêu cầu lưu trữ**  
Công ty muốn quản lý thông tin sản phẩm (tên, số lượng, giá), khách hàng (tên, ngày sinh, liên hệ, địa chỉ, điểm thưởng), đơn hàng (ngày đặt, trạng thái, ghi chú, ngày giao, shipper), và chi tiết từng sản phẩm trong mỗi đơn hàng.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750004860462/fa74f207-9cfb-43ca-b478-3a5856a6053e.png align="center")

**2\. Phát hiện vấn đề quan hệ nhiều-nhiều**  
Nếu chỉ liên kết trực tiếp khách hàng với sản phẩm, sẽ phát sinh lặp dữ liệu và khó quản lý: một khách hàng có thể mua nhiều sản phẩm, một sản phẩm bán cho nhiều khách hàng. Cách này dẫn tới dữ liệu bị dư thừa và khó kiểm soát khóa chính/phụ.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750005014388/abc37c86-7c89-4f9e-8094-497293685aca.png align="center")

**3\. Phân tích và giải quyết bằng bảng trung gian**  
Nhận ra cần thêm thực thể “Order” (Đơn hàng) và “Order Detail” (Chi tiết đơn hàng) để tách biệt quan hệ nhiều-nhiều giữa khách hàng và sản phẩm.

* Order lưu thông tin đơn hàng, liên kết với khách hàng.
    
* Order Detail lưu từng sản phẩm trong đơn hàng, số lượng, đơn giá, liên kết với Order và Product bằng khóa ngoại.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750005038959/08b718d3-cde9-4858-a57e-be7f26c8e875.png align="center")

**4\. Xây dựng sơ đồ ERD hoàn chỉnh**  
Sau khi thêm Order và Order Detail, sơ đồ ERD trở nên rõ ràng, dễ mở rộng:

* Customer (Khách hàng) –&lt; Order (Đơn hàng) –&lt; Order Detail (Chi tiết đơn hàng) &gt;– Product (Sản phẩm).
    
* Bổ sung các thực thể phụ như Shipper, Order Status nếu cần
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750005074105/acdbf35d-d02e-4824-9c86-4944975eb081.png align="center")

**5\. Minh họa bằng ví dụ dữ liệu**  
Đưa ra bảng mẫu cho từng thực thể: khách hàng, sản phẩm, đơn hàng, chi tiết đơn hàng… để người đọc hình dung dữ liệu thực tế sẽ được lưu thế nào và các khóa chính/ngoại liên kết ra sao

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750005090916/f53911b5-2b10-4c5e-a612-ae666429e228.png align="center")

## Triển khai sơ đồ ER

1\. Tổng quan chuyển ERD sang bảng dữ liệu

* **Nội dung:** Giới thiệu ý nghĩa của việc chuyển từ ERD sang các bảng thực tế trong DBMS, các nguyên tắc chung (mỗi thực thể thành một bảng, xác định khóa chính, khóa ngoại…).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750036208195/e111e337-4d55-4bcc-9f30-961a17906316.png align="center")

2. **Xác định khóa chính, khóa ngoại**:  
    Đặt khóa chính (primary key) cho từng bảng, xác định các khóa ngoại (foreign key) để liên kết các bảng với nhau, đảm bảo ràng buộc toàn vẹn dữ liệu
    
3. **Cài đặt quan hệ một-nhiều, nhiều-nhiều**:
    
    * Với quan hệ 1-N: khóa ngoại nằm ở bảng “nhiều”.
        
    * Với quan hệ N-N: tạo bảng trung gian (ví dụ: order\_items) chứa khóa ngoại của hai bảng liên quan, và có thể thêm các thuộc tính riêng (quantity, unit\_price)
        
4. Thứ tự tạo bảng trong DBMS
    
    * Nên tạo các bảng không phụ thuộc (products, customers, shippers, order\_statuses) trước vì chúng không có khóa ngoại, nên có thể tạo độc lập mà không gặp lỗi ràng buộc dữ liệu. Sau đó mới tạo các bảng có khóa ngoại như orders và order\_items, vì các bảng này cần tham chiếu đến các bảng đã có sẵn để đảm bảo toàn vẹn dữ liệu và tránh lỗi khi định nghĩa khóa ngoại[.](https://tecadmin.net/creating-a-table-with-foreign-keys-in-mysql/)[  
        ](https://airbyte.com/data-engineering-resources/database-schema-examples)Làm như vậy giúp quá trình tạo bảng diễn ra suôn sẻ và đảm bảo các mối liên kết giữa bảng được thiết lập chính xác ngay từ đầu.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750036488459/6fd745f3-03c5-4513-a4a7-7e4829a927cc.png align="center")

5. **Tạo bảng bằng lệnh SQL**:  
    Các slide trình bày ví dụ lệnh SQL tạo bảng cho từng entity, xác định kiểu dữ liệu, ràng buộc NOT NULL, AUTO\_INCREMENT, PRIMARY KEY, FOREIGN KEY, v.v
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750036527181/dc0440ea-1e46-44c5-bb2a-b00bd7dfefdd.png align="center")

## Database Normalization – Chuẩn hóa dữ liệu trong thiết kế CSDL

## [1](https://bhk.vn/chuan-hoa-co-so-du-lieu-dinh-nghia-va-phan-loai/). Chuẩn hóa dữ liệu là gì?

Chuẩn hóa dữ liệu (database normali[z](https://bhk.vn/chuan-hoa-co-so-du-lieu-dinh-nghia-va-phan-loai/)ation) là quá trình tổ chức [d](https://bhk.vn/chuan-hoa-co-so-du-lieu-dinh-nghia-va-phan-loai/)ữ liệu trong cơ sở dữ liệu nhằm loại bỏ dư thừa, giảm trùng lặp và đảm bảo tính toàn vẹn dữ li[ệu](https://viblo.asia/p/dbms-normalization-easy-chuan-hoa-trong-thiet-ke-database-relationship-n1j4lOrAVwl). Quá trình này chia các bảng lớn thành các bảng nhỏ hơn, li[ê](https://viblo.asia/p/dbms-normalization-easy-chuan-hoa-trong-thiet-ke-database-relationship-n1j4lOrAVwl)[n](https://funix.edu.vn/chia-se-kien-thuc/chuan-hoa-cac-quan-he-ve-cac-dang-chuan-co-ban/) kết với nhau qua các mối q[u](https://viblo.asia/p/dbms-normalization-easy-chuan-hoa-trong-thiet-ke-database-relationship-n1j4lOrAVwl)[a](https://funix.edu.vn/chia-se-kien-thuc/chuan-hoa-cac-quan-he-ve-cac-dang-chuan-co-ban/)n hệ, giúp dữ liệu dễ bảo trì, truy vấn hiệu quả và hạn chế lỗi khi cập nhật

## 2\. Vì sao cần chuẩn hóa?

Nếu không chuẩn hóa, cơ sở dữ liệu dễ gặp các bất thường (anomaly):

* **Update anomaly:** Khi cập nhật một thông tin lặp ở nhiều nơi, nếu sót sẽ gây sai lệch dữ liệu.
    
* **Insert anomaly:** Không thể thêm dữ liệu mới nếu thiếu thông tin ở cột khác (ví dụ, muốn thêm môn học mới nhưng chưa có sinh viên đăng ký).
    
* **Delete anomaly:** Xóa một dòng có thể vô tình làm mất thông tin quan trọng khác (ví dụ, xóa sinh viên cuối cùng học một môn sẽ mất luôn thông tin về môn đó
    

## 3\. Các dạng chuẩn hóa cơ bản

## a. Dạng chuẩn 1NF (First Normal Form)

* **Yêu cầu:** Mỗi ô chỉ chứa một giá trị nguyên tử, không có nhóm lặp, mỗi hàng là duy nhất
    
* **Ví dụ:** Một bảng có cột số điện thoại, mỗi ô chỉ chứa một số, không phải danh sách nhiều số.
    

**Minh họa:**

* Trước:
    
    | **StudentID** | **Name** | **Phone** |
    | --- | --- | --- |
    | 101 | Vinh | 19001080,19001081 |
    
* Sau:
    
    | **StudentID** | **Name** | **Phone** |
    | --- | --- | --- |
    | 101 | Vinh | 19001080 |
    | 101 | Vinh | 19001081 |
    

## b. Dạng chuẩn 2NF (Second Normal Form)

* **Yêu cầu:** Đạt 1NF và mọi thuộc tính không khóa phải phụ thuộc hoàn toàn vào khóa chính (loại bỏ phụ thuộc từng phần)
    
* **Áp dụng:** Thường gặp khi bảng có khóa chính phức hợp (composite key).
    
* **Ví dụ:**
    
    * Trước:
        
        | **OrderID** | **ProductID** | **ProductName** | **Quantity** |
        | --- | --- | --- | --- |
        | 1 | 101 | Laptop | 2 |
        
        * Ở đây, ProductName chỉ phụ thuộc vào ProductID, không phải vào cả OrderID và ProductID.
            
    * Sau:
        
        * Tách thành hai bảng:
            
            | **OrderID** | **ProductID** | **Quantity** |
            | --- | --- | --- |
            | 1 | 101 | 2 |
            | ProductID | ProductName |  |
            | \----------- | \------------- |  |
            | 101 | Laptop |  |
            

c. Dạng chuẩn 3NF (Third Normal Form)

* **Yêu cầu:** Đạt 2NF và không có phụ thuộc bắc cầu (transitive dependency) giữa các thuộc tính không khóa.
    
* **Giải thích:** Mọi thuộc tính không khóa chỉ phụ thuộc vào khóa chính, không phụ thuộc qua một thuộc tính khác.
    
* **Ví dụ:**
    
    * Trước:
        
        | **StudentID** | **Name** | **Zipcode** | **City** |
        | --- | --- | --- | --- |
        | 1 | Vinh | 94000 | CanTho |
        
        * City phụ thuộc vào Zipcode, Zipcode phụ thuộc vào StudentID.
            
    * Sau:
        
        * Tách thành hai bảng:
            
            | **StudentID** | **Name** | **Zipcode** |
            | --- | --- | --- |
            | 1 | Vinh | 94000 |
            | Zipcode | City |  |
            | \--------- | \-------- |  |
            | 94000 | CanTho |  |
            

## d. Dạng chuẩn BCNF, 4NF, 5NF

## **BCNF (Boyce–Codd Normal Form)**

* **Định nghĩa:**  
    Một bảng đạt chuẩn BCNF nếu với mọi phụ thuộc hàm X → Y, thì X là siêu khóa của bảng đó.  
    Nói cách khác, mọi phụ thuộc hàm không tầm thường đều phải có vế trái là siêu khóa.
    
* **Ý nghĩa:**  
    BCNF là phiên bản chặt hơn của 3NF, loại bỏ các trường hợp ngoại lệ mà 3NF chưa xử lý hết, đặc biệt với các bảng có nhiều candidate key hoặc phụ thuộc hàm phức tạp.
    
* **Ví dụ:**  
    Giả sử bảng đăng ký môn học:
    
    | **StudentID** | **CourseID** | **InstructorID** | **InstructorName** |
    | --- | --- | --- | --- |
    | 101 | CS101 | I01 | John Smith |
    | 102 | CS101 | I01 | John Smith |
    | 103 | MA201 | I02 | Alice Brown |
    
    * Phụ thuộc: InstructorID → CourseID, InstructorID → InstructorName.
        
    * Candidate key: (StudentID, CourseID) và (StudentID, InstructorID).
        
    * InstructorID không phải là siêu khóa, nên bảng này vi phạm BCNF và cần tách thành hai bảng:
        
        * Đăng ký: (StudentID, InstructorID)
            
        * Giảng viên: (InstructorID, CourseID, InstructorName)
            

## **4NF (Fourth Normal Form)**

* **Định nghĩa:**  
    Một bảng đạt 4NF nếu:
    
    * Đã đạt BCNF.
        
    * Không có phụ thuộc đa trị phi tầm thường mà vế trái không phải là siêu khóa.
        
* **Phụ thuộc đa trị (multivalued dependency):**  
    Xảy ra khi một thuộc tính có thể có nhiều giá trị độc lập với các thuộc tính khác trong cùng bảng.
    
* **Ví dụ:**  
    Bảng lưu thông tin sinh viên, các môn học và sở thích:
    
    | **StudentID** | **Course** | **Hobby** |
    | --- | --- | --- |
    | 1 | Math | Basketball |
    | 1 | Math | Reading |
    | 1 | Science | Basketball |
    | 1 | Science | Reading |
    
    * Ở đây, StudentID quyết định độc lập cả Course và Hobby → phụ thuộc đa trị.
        
    * Để đạt 4NF, tách thành hai bảng:
        
        * Student\_Courses(StudentID, Course)
            
        * Student\_Hobbies(StudentID, Hobby)
            

## **5NF (Fifth Normal Form)**

* **Định nghĩa:**  
    Một bảng đạt 5NF nếu:
    
    * Đã đạt 4NF.
        
    * Mọi phép phân rã (decomposition) của bảng thành các bảng con đều là phân rã không mất mát (lossless join), nghĩa là khi nối lại không bị mất hoặc tạo ra dữ liệu sai.
        
* **Ý nghĩa:**  
    5NF xử lý các quan hệ phức tạp hơn, đảm bảo dữ liệu không bị lặp lại hoặc mất mát khi phân rã bảng nhiều chiều.
    
* **Ví dụ:**  
    Bảng lưu thông tin Dealer, Product, Supplier:
    
    | **Dealer** | **Product** | **Supplier** |
    | --- | --- | --- |
    | D1 | P1 | S1 |
    | D1 | P2 | S1 |
    | D2 | P1 | S1 |
    | D2 | P2 | S2 |
    | D1 | P1 | S2 |
    | D2 | P1 | S2 |
    
    * Nếu tồn tại các phụ thuộc join phức tạp, cần phân rã thành các bảng nhỏ hơn (Dealer-Product, Product-Supplier, Dealer-Supplier) để đảm bảo khi join lại vẫn đúng dữ liệu gốc, không dư thừa hoặc thiếu thông tin.
        

## 4\. Quy trình chuẩn hóa thực tế

**Bước 1: Kiểm tra bảng đã đạt 1NF chưa (cột lặp, giá trị không nguyên tử)**

* Đảm bảo mỗi cột chỉ chứa một giá trị duy nhất (nguyên tử), không có danh sách, mảng hoặc nhóm lặp trong một ô.
    
* Nếu phát hiện cột chứa nhiều giá trị (ví dụ: số điện thoại tách bằng dấu phẩy), cần tách thành nhiều dòng hoặc bảng riêng.
    

**Bước 2: Xem xét phụ thuộc từng phần để chuẩn hóa lên 2NF**

* Kiểm tra các bảng có khóa chính phức hợp (nhiều cột).
    
* Loại bỏ các thuộc tính không khóa chỉ phụ thuộc vào một phần của khóa chính, tách chúng ra bảng riêng để đảm bảo mọi thuộc tính không khóa đều phụ thuộc hoàn toàn vào toàn bộ khóa chính.
    

**Bước 3: Xem xét phụ thuộc bắc cầu để chuẩn hóa lên 3NF**

* Kiểm tra xem có thuộc tính không khóa nào phụ thuộc vào một thuộc tính không khóa khác không (phụ thuộc bắc cầu).
    
* Nếu có, tách các thuộc tính này sang bảng mới để đảm bảo mọi thuộc tính không khóa chỉ phụ thuộc trực tiếp vào khóa chính.
    

**Bước 4: Nếu cần, tiếp tục chuẩn hóa lên BCNF, 4NF, 5NF**

* Xác định các phụ thuộc hàm phức tạp mà 3NF chưa xử lý hết (BCNF).
    
* Kiểm tra và loại bỏ các phụ thuộc đa trị (4NF), đảm bảo không có thuộc tính nào độc lập nhận nhiều giá trị cho một khóa.
    
* Nếu bảng có các quan hệ phức tạp, phân rã thêm để đảm bảo khi ghép các bảng con lại không mất mát dữ liệu (5NF).
    

## 5\. Lưu ý khi chuẩn hóa

* **Không phải lúc nào cũng cần chuẩn hóa tối đa**: Đôi khi, để tối ưu hiệu năng truy vấn (OLAP), có thể chấp nhận phi chuẩn hóa một số bảng.
    
* Chuẩn hóa giúp dữ liệu nhất quán, dễ bảo trì, giảm lỗi khi cập nhật.