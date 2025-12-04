---
title: "Blog 1"
date: "2025-09-09T19:53:52+07:00"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
Lưu ý: Bài viết dưới đây là bản dịch đã được diễn giải từ một Blog Cơ sở Dữ liệu của AWS.  
Vui lòng **không sao chép nguyên văn** vào bất kỳ báo cáo chính thức nào.
{{% /notice %}}

# Tối Ưu Hóa Chuyển Đổi & Kiểm Thử Mã Nguồn Từ Microsoft SQL Server và Oracle Sang PostgreSQL Bằng Amazon Bedrock  
**Tác giả:** Swanand Kshirsagar, Jose Amado-Blanco, Viswanatha Shastry Medipalli  
**Xuất bản:** Ngày 02 tháng 06 năm 2025  
**Chuyên mục:** Amazon Aurora, Amazon RDS, AWS Bedrock, Schema Conversion, PostgreSQL, Hướng dẫn Kỹ thuật

---

Các tổ chức ngày nay đang hiện đại hóa cơ sở hạ tầng cơ sở dữ liệu của mình bằng cách di chuyển từ các công cụ cũ như **Microsoft SQL Server** và **Oracle** sang **PostgreSQL**, một công cụ mã nguồn mở mang lại lợi ích về chi phí, tính linh hoạt và khả năng mở rộng mạnh mẽ.

Di chuyển sang PostgreSQL không chỉ giảm chi phí cấp phép mà còn thúc đẩy đổi mới thông qua bộ tính năng phong phú của PostgreSQL.  
Bài blog này giải thích cách **AI tạo sinh (generative AI) của Amazon Bedrock** có thể tăng tốc và đơn giản hóa quy trình chuyển đổi và kiểm thử mã nguồn cơ sở dữ liệu trong quá trình di chuyển.

Vì **Amazon Q Developer** được xây dựng trên các mô hình của Bedrock, nên phương pháp tiếp cận tương tự cũng có thể được áp dụng khi sử dụng Amazon Q Developer.

---

# Thách Thức trong Di Chuyển Cơ Sở Dữ Liệu Dị Thể (Heterogeneous Database Migration)

Di chuyển từ SQL Server hoặc Oracle sang PostgreSQL thường liên quan đến:

### **1. Chuyển Đổi Schema (Lược đồ)**  
Dịch các bảng, views, ràng buộc, chỉ mục và kiểu dữ liệu sang định dạng tương thích với PostgreSQL.

### **2. Chuyển Đổi Logic Kinh Doanh**  
Chuyển đổi các stored procedures, triggers, functions và logic xử lý lỗi sang PL/pgSQL.

### **3. Di Chuyển Dữ Liệu**  
Thực hiện các quy trình ETL (Trích xuất, Biến đổi, Tải) trong khi đảm bảo độ chính xác, tính nhất quán và khả năng tương thích kiểu dữ liệu.

### **4. Cập Nhật Mã Nguồn Ứng Dụng**  
Điều chỉnh các truy vấn SQL hoặc cấu hình ORM (Object-Relational Mapping) để hoạt động chính xác với PostgreSQL.

### **5. Tinh Chỉnh Hiệu Suất**  
Tối ưu hóa SQL, lập chỉ mục và kế hoạch thực thi trong công cụ PostgreSQL mới.

Các nhiệm vụ này đòi hỏi nỗ lực thủ công và chuyên môn đáng kể—và làm tăng rủi ro nếu lỗi không được phát hiện.

---

# Amazon Bedrock Hỗ Trợ Như Thế Nào

Amazon Bedrock có thể tự động hóa và tối ưu hóa nhiều bước di chuyển bằng cách sử dụng **AI tạo sinh**, giảm nỗ lực, thời gian và rủi ro.

### **Tự Động Chuyển Đổi Schema & Mã Nguồn**

Bedrock có thể phân tích mã SQL Server hoặc Oracle và tạo ra các thành phần tương thích với PostgreSQL:

- Định nghĩa bảng  
- Stored procedures & functions  
- Triggers  
- Logic xử lý ngoại lệ (Exception handling)  

### **Biến Đổi Dữ Liệu Dựa Trên AI**

Các mô hình của Bedrock xác định các điều chỉnh cần thiết cho kiểu ngày, kiểu số, kiểu tiền tệ và các khác biệt về cấu trúc để phù hợp với PostgreSQL.

### **Thông Tin Chuyên Sâu về Khả Năng Tương Thích Mã Nguồn**

Bedrock phát hiện:

- Các hàm SQL Server không được hỗ trợ  
- Các cấu trúc PL/SQL của Oracle  
- Cú pháp độc quyền  
- Sự khác biệt về hành vi giao dịch (Transaction behavior)  

…và đề xuất các lựa chọn thay thế tương đương trong PostgreSQL.

### **Kiểm Thử & Xác Nhận Thông Minh**

Bedrock có thể tạo ra:
- Các trường hợp kiểm thử (Test cases)  
- Các script xác nhận (Validation scripts)  
- Phân tích độ bao phủ mã nguồn (Code coverage analysis)  

Điều này đảm bảo mã nguồn đã chuyển đổi đáp ứng các yêu cầu về chức năng và hiệu suất trước khi triển khai sản xuất.

### **Kỹ Thuật Prompt để Đạt Độ Chính Xác**

Các prompt được thiết kế tốt có thể buộc Bedrock phải:

- Giữ nguyên quy ước đặt tên  
- Tuân thủ các phương pháp hay nhất của PostgreSQL  
- Duy trì độ chính xác của logic kinh doanh  
- Giảm sự mơ hồ  

Việc tinh chỉnh prompt lặp đi lặp lại giúp cải thiện độ chính xác của quá trình chuyển đổi và giảm công việc thủ công.

---

# Ví Dụ: Chuyển Đổi Procedure SQL Server Sang Function PostgreSQL

Sử dụng Amazon Bedrock:

1. Mở **Amazon Bedrock Console → Playgrounds → Chat/Text**  
2. Chọn **Anthropic → Claude 3.5 Sonnet**  
3. Dán prompt yêu cầu Bedrock chuyển đổi procedure SQL Server sang function PostgreSQL.

Bedrock tạo ra:

- Một function `plpgsql` của PostgreSQL  
- Logic tương đương  
- Xử lý lỗi bằng cách sử dụng các quy ước của PostgreSQL  
- Một bộ đầy đủ các trường hợp kiểm thử bao gồm:
  - Cập nhật hợp lệ  
  - Tham số không hợp lệ  
  - Không có nhân viên đủ điều kiện  
  - Giới hạn tăng tối đa  
  - Tăng dựa trên tỷ lệ phần trăm  
  - Nhân viên không hoạt động  
  - Thâm niên không đủ  
  - Nhiều nhân viên  

Nếu phản hồi ban đầu thay đổi quy ước đặt tên (ví dụ: chữ thường hoặc dấu gạch dưới), bạn có thể yêu cầu Bedrock tạo lại trong khi **giữ nguyên tên gốc**.

---

# Phân Tích Độ Bao Phủ Kiểm Thử (Test Coverage Analysis)

Bedrock cũng có thể phân tích các trường hợp kiểm thử đã tạo và cung cấp **phân tích độ bao phủ**, cho biết phần nào của mã nguồn được kiểm thử:

- Xác nhận đầu vào  
- Tính toán lương  
- Các quy tắc đủ điều kiện  
- Các thao tác cập nhật  
- Ghi log  
- Xử lý ngoại lệ  
- Logic kết quả trả về  

Các kiểm thử bổ sung được đề xuất có thể bao gồm:

- Các điều kiện ngày tháng biên (Edge date conditions)  
- Các giá trị số lớn  
- Lỗi cơ sở dữ liệu được mô phỏng  

Đối với độ bao phủ chính xác hoàn toàn, các công cụ như **pgTAP** được khuyến nghị.

---

# Tạo Các Đối Tượng Cơ Sở Dữ Liệu Hỗ Trợ

Theo yêu cầu, Bedrock có thể tạo ra:

- Các script `CREATE TABLE` (Employees, SalaryUpdateLog)  
- Dữ liệu kiểm thử mẫu  
- Các script khởi tạo môi trường  

Điều này giúp bạn tái tạo hoàn chỉnh function ví dụ cục bộ trong quá trình kiểm thử di chuyển.

---

# Tự Động Hóa Thực Thi Kiểm Thử Trên Nguồn & Đích

Bạn có thể tích hợp API của Bedrock vào một ứng dụng tùy chỉnh để:

- Chạy các trường hợp kiểm thử đối với SQL Server (nguồn) và PostgreSQL (đích)  
- Tự động so sánh kết quả  
- Xác định sự khác biệt về logic  
- Đo lường sự khác biệt về hiệu suất  
- Tạo báo cáo tóm tắt di chuyển  

Điều này loại bỏ việc xác minh thủ công và tăng tốc hiện đại hóa.

AWS Database Migration Service (AWS DMS) Schema Conversion accelerators cũng có thể hỗ trợ các quy trình di chuyển và chuyển đổi mã nguồn.

---

# Kết Luận

AWS cung cấp một bộ công cụ và dịch vụ mạnh mẽ để hiện đại hóa các cơ sở dữ liệu doanh nghiệp.  
Bài blog này đã chứng minh cách Amazon Bedrock có thể:

- Chuyển đổi mã SQL Server/Oracle sang PostgreSQL  
- Tạo ra các trường hợp kiểm thử hoàn chỉnh  
- Phân tích độ bao phủ mã nguồn  
- Tạo ra schema và dữ liệu kiểm thử hỗ trợ  
- Cải thiện độ chính xác thông qua tinh chỉnh prompt 

Bằng cách tích hợp Bedrock vào chiến lược di chuyển của mình, các tổ chức có thể giảm đáng kể:

- Thời gian di chuyển  
- Chi phí vận hành  
- Rủi ro lỗi logic hoặc tương thích  

Để bắt đầu với Amazon Bedrock, hãy tham khảo **Bắt đầu với Amazon Bedrock** trong tài liệu AWS.