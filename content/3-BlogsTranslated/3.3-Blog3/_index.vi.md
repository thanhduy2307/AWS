---
title: "Blog 3"
date: "2025-09-09T19:53:52+07:00"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# Cách Blocksee Xây Dựng CRM Web3 Với Dữ Liệu Blockchain Từ Amazon Managed Blockchain (AMB) Query  
**Tác giả:** Forrest Colyer & AJ Park  
**Xuất bản:** Ngày 06 tháng 03 năm 2024  
**Chuyên mục:** Amazon Managed Blockchain, Blockchain, Customer Solutions, Foundational (100)

---

## Về Các Tác Giả

**AJ Park** là Quản lý Sản phẩm trong nhóm Amazon Managed Blockchain tại AWS.  
Với hơn 20 năm kinh nghiệm trong lĩnh vực bảo vệ và lưu trữ dữ liệu với vai trò là kỹ sư phần mềm và quản lý sản phẩm, ông đam mê xây dựng các giải pháp blockchain và Web3 cho khách hàng.

**Forrest Colyer** là Trưởng nhóm Kiến trúc Giải pháp Chuyên biệt về Web3/Blockchain, nhóm này hỗ trợ dịch vụ Amazon Managed Blockchain (AMB).  
Ông làm việc với khách hàng qua mọi giai đoạn áp dụng blockchain—từ thử nghiệm ý tưởng (proof-of-concept) đến vận hành thực tế—cung cấp chuyên môn kỹ thuật và định hướng chiến lược để triển khai các khối lượng công việc blockchain có tác động lớn.

---

# Tổng Quan

**Blocksee** cung cấp nền tảng Quản lý Quan hệ Khách hàng (CRM) và tương tác người dùng tập trung vào Web3, mang lại thông tin chuyên sâu phong phú cho các nhà tiếp thị NFT và tiền điện tử.  
Bằng cách nhúng đoạn mã đơn giản vào trang web hoặc sử dụng API, Blocksee cho phép các nhà tiếp thị thu thập dữ liệu về những người dùng tương tác với thành viên kỹ thuật số, vé sự kiện và tài sản khuyến mãi.

Được hỗ trợ bởi các dịch vụ AWS—bao gồm **Amazon Managed Blockchain (AMB)**—Blocksee giúp các thương hiệu xây dựng:

- Chương trình khách hàng thân thiết  
- Nội dung giới hạn bằng token (Token-gated content)  
- Hành trình khách hàng động  
- Tạo ví tự động qua email  
- Thanh toán onramp để nhận tài sản kỹ thuật số (ví dụ: NFT)

Để cho phép phân tích chuyên sâu về hoạt động của tài sản kỹ thuật số và tương tác của người dùng, Blocksee yêu cầu lượng lớn **dữ liệu on-chain** từ các blockchain công khai như Ethereum, bao gồm:

- Số dư token hiện tại và lịch sử  
- Quyền sở hữu token có thể thay thế (fungible) và không thể thay thế (NFT)  
- Tương tác của người dùng với các ứng dụng Web3 và hợp đồng thông minh  

Blocksee đã đánh giá nhiều phương pháp kỹ thuật—từ tự vận hành toàn bộ cơ sở hạ tầng blockchain đến sử dụng các nhà cung cấp bên thứ ba.  
Cơ sở hạ tầng tự quản lý được chứng minh là quá tốn kém và nặng nề về mặt vận hành do:

- Nhu cầu tính toán (compute), lưu trữ và mạng cao  
- Quy trình ETL (Trích xuất, Biến đổi, Tải) và hoạt động lập chỉ mục tiêu tốn tài nguyên  
- Nỗ lực của nhà phát triển đáng kể, làm chậm quá trình phân phối tính năng sản phẩm cốt lõi  

Các nhà cung cấp dữ liệu blockchain bên thứ ba cũng không đủ đáp ứng, với các thách thức như:

- Thời gian hoạt động (uptime) không đáng tin cậy  
- Chất lượng dữ liệu kém  
- Hiệu năng chậm  
- Chi phí cao và khó dự đoán  

---

# Tại Sao Blocksee Chọn Amazon Managed Blockchain (AMB) Query

Cuối cùng, Blocksee đã áp dụng **AMB Query**, một API dữ liệu blockchain hợp nhất cho nhiều mạng công khai.

Lợi ích của việc chuyển đổi:

### ✔ Độ tin cậy cao hơn### ✔ Chi phí thấp hơn và dễ dự đoán  
### ✔ Hiệu năng nhanh hơn  
### ✔ Một API duy nhất, nhất quán cho nhiều blockchain  

Điều này cho phép Blocksee rút ngắn chu kỳ phát hành sản phẩm và giảm chi phí kỹ thuật.

Tuyên bố từ **Eric Forst, Đồng sáng lập & Giám đốc điều hành (CEO) của Blocksee**, nhấn mạnh sự thay đổi này:

> “Trước khi sử dụng Amazon Managed Blockchain, nhóm của chúng tôi phải tổng hợp dữ liệu từ nhiều nhà cung cấp RPC khác nhau, dẫn đến cấu hình API phức tạp và chi phí giám sát.  
> AMB đã thay đổi mọi thứ — quyền truy cập nhanh và ổn định vào dữ liệu blockchain đã giúp chúng tôi hợp lý hóa hệ thống của mình và dựa vào một cơ sở hạ tầng đáng tin cậy hơn.”

---

# Cách Blocksee Sử Dụng AMB Query

Khi các nhà tiếp thị hoặc quản lý dự án mở công cụ Blocksee CRM, dữ liệu số dư token cho các địa chỉ blockchain (người dùng) được hiển thị ngay lập tức và kết hợp với các dữ liệu ngữ cảnh bổ sung như phân tích hành vi được hỗ trợ bởi AI.

Blocksee sử dụng **ListTokenBalances API** từ AMB Query để truy xuất số dư token **ERC-20 và ERC-721**.  
API này cho phép Blocksee:

- Liệt kê tất cả số dư token thuộc về một ví hoặc hợp đồng  
- Liệt kê tất cả chủ sở hữu token cho một hợp đồng thông minh nhất định  
- Liệt kê số dư cho một token cụ thể trên tất cả các chủ sở hữu  

### ⭐ Kết Quả:  
**Cải thiện hiệu suất 25%**  
**Giảm chi phí 50%**  
so với cơ chế truy xuất dữ liệu token trước đây của Blocksee.

CTO của Blocksee, **Matt Kotnik**, chia sẻ thêm thông tin chi tiết:

> “Chúng tôi nhận thấy sự cải thiện đáng kể về thời gian tải—nhanh hơn hơn 25%—khi sử dụng ListTokenBalances API của AMB Query.  
> AMB cũng cho phép chúng tôi dễ dàng mở rộng sang các blockchain bổ sung nhờ thiết kế trung lập chuỗi của Amazon.  
> Điều này giúp chúng tôi tập trung nhiều hơn vào sản phẩm cốt lõi và mối quan hệ khách hàng trong khi vẫn dựa vào một đối tác cơ sở hạ tầng đáng tin cậy.”

Vì AMB Query sử dụng một **REST API chuẩn hóa**, việc tích hợp các blockchain mới trong tương lai trở nên đơn giản.  
Cú pháp truy vấn gần như không thay đổi ngay cả khi tìm nạp dữ liệu trên nhiều mạng cùng lúc.

---

# Kết Luận

AMB Query hiện đã có sẵn tại Khu vực **US East (N. Virginia)**, cung cấp:

- Độ trễ dưới giây (Sub-second latency)  
- Khả năng truy cập có thể mở rộng cao vào số dư blockchain và giao dịch lịch sử  
- Không cần vận hành cơ sở hạ tầng blockchain  
- Mô hình giá đơn giản, dễ dự đoán dựa trên các cuộc gọi API  

Khách hàng có thể tin tưởng vào AMB Query để có dữ liệu blockchain hiệu suất cao, đáng tin cậy, đáp ứng nhu cầu của các ứng dụng Web3 thực tế.

Để tìm hiểu thêm:

- Khám phá **Tài liệu AMB Query**  
- Khám phá các dịch vụ AMB khác tại **Amazon Managed Blockchain**