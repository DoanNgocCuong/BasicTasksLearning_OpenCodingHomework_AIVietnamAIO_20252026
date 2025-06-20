---
title: "M01W02T7: Git & GitHub For Version Control"
datePublished: Tue Jun 17 2025 03:40:28 GMT+0000 (Coordinated Universal Time)
cuid: cmbzz6n4i000c02jo17tgd8ur
slug: m01w02t7-git-and-github-for-version-control

---

Trong thời đại phát triển phần mềm hiện đại, quản lý phiên bản (version control) là công cụ không thể thiếu để kiểm soát và cộng tác hiệu quả trên các dự án code. Dù bạn là lập trình viên cá nhân hay thành viên của một nhóm lớn, hiểu và sử dụng Git cùng GitHub sẽ giúp bạn làm chủ quá trình phát triển, bảo vệ lịch sử dự án và làm việc nhóm dễ dàng hơn

# I. Version Control là gì?

Hãy tưởng tượng bạn xây một ngôi nhà, mỗi lần thay đổi gì đó, bạn chụp lại một bức ảnh để nếu có vấn đề, bạn có thể quay lại trạng thái trước đó. Version control cũng giống như vậy với code: nó lưu lại mọi “bức ảnh” của dự án sau mỗi lần thay đổi, cho phép bạn quay lại bất kỳ thời điểm nào nếu cần.

## **Lợi ích của Version Control:**

* ## Theo dõi toàn bộ lịch sử thay đổi của dự án.
    
* Biết ai, khi nào và tại sao thay đổi gì.
    
* Dễ dàng hoàn tác (revert) về phiên bản ổn định nếu gặp lỗi.
    
* Hỗ trợ làm việc nhóm, tránh đè lên công việc của nhau.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750049430215/852687dd-5308-4749-a385-8497488bc8c0.png align="center")

## **1\. Local Version Control System (VCS cục bộ)**

* **Cách hoạt động:**
    
    * Chỉ lưu lịch sử thay đổi trên máy tính cá nhân của từng người dùng.
        
    * Mỗi khi bạn chỉnh sửa file, hệ thống sẽ lưu lại một bản sao (snapshot) của file đó vào một thư mục ẩn trên máy.
        
* **Ưu điểm:**
    
    * Đơn giản, dễ sử dụng cho cá nhân hoặc dự án nhỏ.
        
    * Không cần kết nối mạng, mọi thứ đều trên máy local.
        
* **Nhược điểm:**
    
    * **Không hỗ trợ làm việc nhóm:** Không thể chia sẻ thay đổi với người khác một cách tự động.
        
    * **Rủi ro mất dữ liệu:** Nếu máy tính bị hỏng hoặc mất, toàn bộ lịch sử dự án cũng mất theo.
        
    * **Khó kiểm soá**[**t**](https://www.linkedin.com/pulse/differentiate-between-centralized-distributed-version-control-ejv2c) **phiên bản khi nhiều người cùng làm việc.**
        

## **2\. Centralized Version Control System (CVCS – Hệ thống tập trung)**

* **Cách hoạt động:**
    
    * C[ó](https://www.linkedin.com/pulse/differentiate-between-centralized-distributed-version-control-ejv2c) một **máy chủ trung tâm** (central server) lưu trữ toàn bộ lịch sử và mã nguồn dự án.
        
    * Mọi thành viên trong nhóm phải kết nối tới máy chủ này để lấy code về, commit thay đổi và cập [n](https://www.linkedin.com/pulse/differentiate-between-centralized-distributed-version-control-ejv2c)hật phiên bản mới.
        
* **Ưu điểm:**
    
    * **Kiểm soát tập trung:** Dễ quản lý, kiểm soát quyền truy cập và lịch sử thay đổi.
        
    * **Phù hợp cho nhóm nhỏ hoặc môi trường kiểm soát chặt chẽ.**
        
* **Nhược điểm:**
    
    * **Phụ thuộc vào máy chủ:** Nếu server gặp sự cố hoặc mất mạng, mọi người không thể làm việc hoặc truy cập lịch sử dự án.
        
    * **Điểm yếu duy nhất:** Nếu server bị mất dữ liệu mà không có backup, toàn bộ lịch sử dự án có thể bị mất.
        
    * **Khó khăn khi làm việc offline:** Mọi thao tác đều cần kết nối tới server[,](https://about.gitlab.com/topics/version-control/what-is-centralized-version-control-system/) tốc độ chậm nếu mạng yếu.
        

## **3\. Distributed Version Control System (DVCS – Hệ thống phân tán)**

* **Cách hoạt** **động**[**:**](https://www.linkedin.com/pulse/differentiate-between-centralized-distributed-version-control-ejv2c)
    
    * **Mỗi người dùng có một bản sao đầy đủ** của toàn bộ repository (bao gồm cả lịch sử thay đổi) trên máy tính cá nhân.
        
    * Người dùng có thể commit, tạo nhánh[,](https://www.linkedin.com/pulse/differentiate-between-centralized-distributed-version-control-ejv2c) merge... hoàn toàn offline. Khi cần chia sẻ thay đổi, họ push/pull lên server chung (ví dụ GitHub).
        
* **Ưu điểm:**
    
    * **Làm việc offline:** Hầu hết thao tác không cần mạng, chỉ cần khi đồng bộ với nhóm.
        
    * **An toàn dữ liệu:** Nếu server bị hỏng, mọi người đều có bản sao đầy đủ [đ](https://www.tutorialspoint.com/difference-between-centralized-version-control-and-distributed-version-control)ể khôi phục dự án.
        
    * **Hỗ** **trợ** **branching, merging mạnh mẽ:** Phù hợp cho dự án lớn, nhóm đông người, open source.
        
    * **Tốc độ nhanh:** Vì thao tác chủ yếu trên má[y](https://blog.devart.com/centralized-vs-distributed-version-control.html) local.
        
* **Nhược điểm:**
    
    * **Khó học hơn:** Cần làm quen với nhiều khái niệm mới (branch, merge, pull, push...)[.](https://blog.devart.com/centralized-vs-distributed-version-control.html)
        
    * **Quản** **lý phức** **tạp** **hơn** nếu không có quy trình rõ ràng.
        

# **II. Git là gì?**

## 1\. **Bối cảnh ra đời (2005)**

* [**N**](https://builtin.com/articles/version-control-systems)**guyên nhân:**  
    Năm 2005, cộng đồng phá[t](https://about.gitlab.com/topics/version-control/what-is-centralized-version-control-system/) triển nhân Linux gặp phải mâu thuẫn lớn với công ty BitKeeper – đơn vị cung cấp công cụ quản lý mã nguồn mà nhóm Linux đang sử dụng. BitKeeper thay đổi chính sách cấp phép, dẫn đến việc nhóm phát triển Linux không còn quyền sử dụng miễn phí công cụ này nữa.
    
* **Vấn đề đặt ra:**[  
    ](https://about.gitlab.com/topics/version-control/what-is-centralized-version-control-system/)Dự án Linux là một dự án mã nguồn mở quy mô toàn cầu, cần một hệ thống quản lý phiên bản mạnh mẽ, miễn phí, không phụ thuộc vào bên thứ ba, và phải đáp ứng được tốc độ phát triển cực nhanh cũng như số lượng lập trình viên đón[g](https://blog.devart.com/centralized-vs-distributed-version-control.html) [g](https://builtin.com/articles/version-control-systems)óp rất lớn.
    

## 2\. **Người sáng lập**

* **Linus Torvalds** – cha đẻ của hệ điều hành Linux – đã trực tiếp bắt tay vào thiết kế và phát triển một hệ thốn[g](https://about.gitlab.com/topics/version-control/what-is-centralized-version-control-system/) quản lý phiên bản hoàn toàn mới, với mục tiêu giải [q](https://blog.devart.com/centralized-vs-distributed-version-control.html)u[y](https://builtin.com/articles/version-control-systems)ết triệt để các hạn chế của các hệ thống [c](https://www.tutorialspoint.com/difference-between-centralized-version-control-and-distributed-version-control)ũ và phù hợp với nhu cầu phát triển phần mềm mã nguồn mở quy mô lớn.
    

## 3\. **Mục tiêu thiết** [**k**](https://www.tutorialspoint.com/difference-between-centralized-version-control-and-distributed-version-control)**ế của Git**

* **Nhanh:**  
    Git phải xử lý các thao tác như commit, branch, merge[,](https://blog.devart.com/centralized-vs-distributed-version-control.html) và chuyển đổi giữa các phiên bản cực kỳ nhanh chóng, kể cả với dự án có hàng triệu dòng code.
    
* **Đơn giản:**  
    Cấu trúc dữ liệu và thao tác của Git phải dễ hiểu, dễ sử dụng, thuận tiện cho cả cá nhân lẫn n[h](https://blog.devart.com/centralized-vs-distributed-version-control.html)ó[m](https://builtin.com/articles/version-control-systems) lớn.
    
* **Dễ phân nhánh:**  
    Việc tạo, chuyển, gộp (merge) nhánh phải nhẹ nhàng, không tốn tài nguyên, khuyến khích phát triển song song và thử nghiệm tính năng mới mà không ảnh hưởng đến nhánh chính.
    
* **Làm việc phân tán:**  
    Mỗi lập trình viê[n](https://blog.devart.com/centralized-vs-distributed-version-control.html) [đ](https://builtin.com/articles/version-control-systems)ều có thể làm việc độc lập trên máy cá nhân với toàn bộ lịch sử dự án, chỉ cần kết nối mạng k[h](https://blog.devart.com/centralized-vs-distributed-version-control.html)i muốn đồng bộ hoặc chia sẻ thay đổi với cộng đồng.
    

## 4\. **Quá trình phát triển và phổ biến**

* Chỉ sau vài tháng phát triển, Git đã trở thành công cụ chính thức của dự án Linux, thay thế hoàn toàn BitKeeper.
    
* Nhờ các đặc tính vượt trội, Git nha[n](https://blog.devart.com/centralized-vs-distributed-version-control.html)h chóng được cộng đồng mã nguồn mở và các công ty công nghệ lớn trên toàn thế giới chấp nhận, sử dụng rộng rãi cho mọi loại dự án – từ nhỏ đến siêu lớn.
    

## 5\. **Ý nghĩa của sự ra đời Git**

* Git không chỉ là một phần mềm quản lý phiên bản, mà còn là một bước ngoặt lớn trong việc phát triển phần mềm hiện đại, đặc biệt là các dự án mã nguồn mở, nơi cộng tác phân tán, kiểm soát lịch sử và bảo vệ dữ liệu là tối quan trọng.
    

## **Các khái niệm cơ bản trong Git:**

* **Repository (repo):** Thư mục chứa toàn bộ mã nguồn và lịch sử thay đổi của dự án.
    
* **Commit:** Lưu lại một “ảnh chụp” trạng thái dự án tại thời điểm đó.
    
* **Branch:** Nhánh phát triển song song, giúp thử nghiệm tính năng mới mà không ảnh hưởng đến mã nguồn chính.
    
* **Merge:** Kết hợp thay đổi từ các nhánh khác nhau.
    
* **Pull:** Lấy về các thay đổi mới nhất từ repo trên mạng về máy cá nhân.
    
* **Push:** Đẩy các thay đổi từ máy cá nhân lên repo trên mạng.
    

## Nguyên lý hoạt động của Git

## **1\. Snapshot thay vì Diff**

* **Khác biệt với VCS cũ:**  
    Các hệ thống quản lý phiên bản truyền thống (như SVN, CVS) chỉ lưu lại các thay đổi (diff) giữa các phiên bản file. Điều này khiến việc phục hồi hoặc xem lại toàn bộ trạng thái dự án ở một thời điểm cụ thể trở nên phức tạp và đôi khi chậm.
    
* **Git lưu “bản chụp” toàn bộ dự án mỗi khi commit:**  
    Thay vì chỉ lưu phần thay đổi, Git sẽ lưu lại một snapshot (ảnh chụp) của toàn bộ dự án ở thời điểm commit. Điều này giúp việc phục hồi, so sánh và quản lý lịch sử dự án trở nên đơn giản, nhanh chóng hơn.
    
* **Tiết kiệm dung lượng:**  
    Nếu một file không thay đổi giữa các lần commit, Git không lưu lại file đó lần nữa mà chỉ tạo liên kết đến bản chụp cũ. Nhờ vậy, Git vừa tiết kiệm dung lượng, vừa giữ được tốc độ xử lý cao.
    

## **2\. Toàn vẹn dữ liệu với SHA-1**

* **Bảo vệ dữ liệu bằng hàm băm SHA-1:**  
    Mỗi đối tượng (file, commit, thư mục...) trong Git đều được gắn một mã định danh duy nhất dài 40 ký tự, được tạo ra bằng thuật toán băm SHA-1. Điều này giúp đảm bảo dữ liệu không bị thay đổi mà không bị phát hiện.
    
* **Thay đổi nội dung, thay đổi mã hash:**  
    Khi nội dung file thay đổi, mã hash cũng thay đổi hoàn toàn. Nhờ vậy, bất kỳ sự thay đổi nào dù nhỏ nhất cũng được Git phát hiện, giúp bảo vệ dữ liệu khỏi bị hỏng hoặc bị chỉnh sửa không hợp lệ.
    

## **3\. Nguyên lý “Offline-first”**

* **Làm việc không cần mạng:**  
    Git cho phép bạn thực hiện hầu hết các thao tác (commit, tạo nhánh, gộp nhánh, xem lịch sử...) ngay trên máy tính cá nhân, không cần kết nối Internet.
    
* **Chỉ cần mạng khi chia sẻ:**  
    Bạn chỉ cần kết nối Internet khi muốn chia sẻ code với người khác (push lên hoặc pull về từ remote repository như GitHub, GitLab...).
    
* **Tăng hiệu suất và linh hoạt:**  
    Nhờ nguyên lý này, Git rất phù hợp cho dự án lớn, nhóm đông người, hoặc khi làm việc ở môi trường mạng không ổn định.
    

## **Vì sao nên dùng Git?**

* Theo dõi lịch sử dự án chi tiết.
    
* Hỗ trợ làm việc nhóm linh hoạt.
    
* Dễ dàng thử nghiệm, phát triển tính năng mới nhờ branching.
    
* Tốc độ xử lý nhanh, hiệu quả ngay cả với dự án lớn.
    

# **III. GitHub là gì?**

GitHub là nền tảng lưu trữ trực tuyến cho các repository Git, đồng thời cung cấp các công cụ cộng tác, quản lý dự án, theo dõi lỗi, review code, và nhiều tính năng mở rộng khác. GitHub giúp bạn chia sẻ, hợp tác và phát triển dự án với cộng đồng lập trình viên toàn cầu.

## **So sánh Git và GitHub**

| **Tính năng** | **Git (Local)** | **GitHub (Online)** |
| --- | --- | --- |
| Mục đích | Quản lý phiên bản mã nguồn trên máy cá nhân | Lưu trữ repo Git trực tuyến, hỗ trợ cộng tác |
| Tạo bởi | Linus Torvalds | GitHub Inc. |
| Cộng tác | Qua repo chia sẻ, cần thiết lập thủ công | Dễ dàng qua pull request, issue, project management |
| Theo dõi lỗi | Không tích hợp | Có hệ thống issue tracking mạnh mẽ |
| Quản lý dự án | Không có | Có Kanban board, milestone, wiki |
| Tính năng mở rộng | Branching, merging, tagging | Pull request, review code, thống kê, marketplace |

# **IV. Quy trình làm việc cơ bản với Git & GitHub**

## **Cài đặt:**

* Linux: `sudo apt install git`
    
* macOS: `xcode-select --install` hoặc tải từ [git-scm.com](http://git-scm.com)
    
* Windows: tải từ [git-scm.com](http://git-scm.com) hoặc `choco install git`
    
    **Cấu hình cơ bản:**
    
    ```bash
    bashgit config --global user.name "Tên Của Bạn"
    git config --global user.email "email@example.com"
    ```
    
    **Alias hữu ích:**
    
    ```bash
    bashgit config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.cm "commit -m"
    ```
    

## Quy trình làm việc cơ bản với Git

* **Khởi tạo repository:**
    
    ```bash
    bashmkdir <ten_du_an>
    cd <ten_du_an>
    git init
    ```
    
* **Sao chép repository từ xa:**
    
    ```bash
    bashgit clone https://github.com/username/repository.git
    ```
    
* **Theo dõi và lưu trữ thay đổi:**
    
    * `git status`, `git add`, `git commit -m "message"`
        
    * Sử dụng `.gitignore` để loại trừ file/thư mục không cần thiết
        
* **Xem lịch sử:**
    
    * `git log`, `git log --oneline --graph --all`
        
* **Hoàn tác thay đổi:**
    
    * `git restore`, `git revert`, `git commit --amend`, `git stash`
        

## Làm việc với remote repository

* **Thêm remote:**
    
    ```bash
    bashgit remote add origin https://github.com/username/repository.git
    ```
    
* **Đồng bộ hóa:**
    
    * `git push origin main`
        
    * `git pull origin main`
        
* **Tagging:**
    
    * Annotated tag: `git tag -a v1.0 -m "Version 1.0"`
        
    * Lightweight tag: `git tag v1.0-beta`
        
    * Đẩy tag: `git push origin v1.0` hoặc `git push origin --tags`
        

## Quản lý nhánh và lịch sử

* **Tạo/chuyển/gộp nhánh:**
    
    ```bash
    bashgit checkout -b feature/ten-tinh-nang
    git merge feature/ten-tinh-nang
    ```
    
* **Giải quyết xung đột:**
    
    * Chỉnh sửa file, `git add .`, `git commit`
        
* **Quản lý nhánh:**
    
    * Liệt kê: `git branch`, `git branch -a`
        
    * Xóa: `git branch -d ten-nhanh`
        
    * Đổi tên: `git branch -m ten-moi`
        
* **Rebase:**
    
    * `git rebase main`
        
    * `git rebase -i HEAD~3`
        

## Cộng tác qua GitHub

* **Thiết lập tài khoản & bảo mật:**
    
    * Đăng ký, xác thực email, tạo SSH key, bật 2FA
        
* **Quy trình Fork & Pull Request:**
    
    1. Fork repository
        
    2. Clone về máy
        
    3. Tạo nhánh mới, commit, push
        
    4. Tạo Pull Request trên GitHub
        
    5. Thảo luận, cập nhật, merge
        
* **Quản lý repository:**
    
    * Tạo README.md, CONTRIBUTING.md, CODE\_OF\_CONDUCT.md
        
    * Thiết lập branch protection, quản lý teams/organization
        

## Tùy chỉnh & mở rộng Git

* **Cấu hình nâng cao:**
    
    * Đổi nhánh mặc định: `git config --global init.defaultBranch main`
        
    * Mẫu commit message, công cụ merge/diff, proxy, credential helper
        
* **Git Attributes:**
    
    * Quản lý line ending, file binary, merge strategy, filter clean/smudge
        
* **Git Hooks:**
    
    * Tự động hóa kiểm tra code, format, CI/CD trước/sau commit/push
        
* **Alias & Scripts:**
    
    * Tạo lệnh tắt, hàm shell cho workflow cá nhân/team
        

# **V. Kết luận**

Git và GitHub là bộ đôi không thể thiếu với bất kỳ ai làm việc với code. Git giúp bạn kiểm soát mọi thay đổi, còn GitHub mở rộng khả năng cộng tác, quản lý dự án và chia sẻ với cộng đồng. Dù bạn là người mới hay đã có kinh nghiệm, hãy bắt đầu sử dụng Git & GitHub để nâng tầm kỹ năng lập trình và làm việc chuyên nghiệp hơn.