---
title: "Blog 2"
date: "2025-09-09T19:53:52+07:00"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


# Ghi Log JSON có Cấu Trúc cho các Hàm .NET Lambda  
**Tác giả:** Norm Johanson  
**Xuất bản:** Ngày 07 tháng 11 năm 2024  
**Chuyên mục:** .NET, AWS Lambda, Developer Tools

---

**Norm Johanson** là một nhà phát triển phần mềm với hơn 25 năm kinh nghiệm xây dựng nhiều loại ứng dụng. Kể từ năm 2010, ông đã làm việc tại AWS, tập trung vào việc cải thiện trải nghiệm cho các nhà phát triển .NET. Bạn có thể tìm thấy ông trên Twitter **@socketnorm** và GitHub **@normj**.

AWS đã công bố **hỗ trợ ghi log JSON có cấu trúc** cho runtime quản lý .NET trong AWS Lambda. Cải tiến này giúp runtime quản lý .NET đồng bộ với các **điều khiển ghi log Lambda** đã được phát hành trước đó, cho phép các nhà phát triển thay đổi định dạng ghi log và cấp độ log thông qua API Lambda.

Việc định dạng thông điệp log dưới dạng **tài liệu JSON** giúp việc tìm kiếm, lọc và phân tích log Lambda trở nên dễ dàng hơn đáng kể—đặc biệt khi giám sát, gỡ lỗi hoặc tạo cảnh báo tự động dựa trên các trường log cụ thể.

---

# Bật Ghi Log JSON có Cấu Trúc

Theo mặc định, log Lambda sử dụng định dạng **văn bản thuần túy (plain text)**.  
Bạn có thể chuyển đổi hàm sang **định dạng log JSON** bằng cách sử dụng các công cụ của AWS, bao gồm:

- AWS Lambda Console  
- Công cụ .NET CLI **Amazon.Lambda.Tools**  
- AWS Tools for PowerShell  
- AWS CLI  

Trong Lambda Console, cấu hình ghi log có sẵn dưới mục:

**Configuration → Monitoring and operations tools → Logging configuration**

Bắt đầu với **Amazon.Lambda.Tools phiên bản 5.11.0**, các switch dòng lệnh mới đã được thêm vào:

- `--log-format`  
- `--log-application-level`  
- `--log-system-level`  
- `--log-group`  

Ví dụ triển khai bật ghi log JSON:

```bash
dotnet tool install -g amazon.lambda.tools
dotnet lambda deploy-function <function-name> --log-format JSON