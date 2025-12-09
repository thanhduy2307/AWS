---
title: "5.4.2 - CRUD việc cần làm  (Event Handler)"
date: 2025-12-09
weight: 1
chapter: false
pre: " <b> 5.4.1. </b> "
---

{{% notice info %}}
📅 **Chức năng:** Hàm này xử lý toàn bộ thao tác Thêm (Create), Xem (Read), Sửa (Update), Xóa (Delete) đối với lịch trình của người dùng.
{{% /notice %}}

# Bước 1: Tạo Lambda Function
* **Tên hàm:** `Aurora_EventHandler`
* **Runtime:** Node.js 18.x
* **Mô tả:** API xử lý CRUD cho bảng Events.

> **Hình ảnh:**
> ![Screenshot: Tạo hàm Aurora_EventHandler](images/lambda-event-create.png)

# Bước 2: Cấu hình IAM Role (Full Access to Events)
Chúng ta cần cấp toàn quyền đọc/ghi trên bảng `AuroraEvents`.
* **Resource:** `arn:aws:dynamodb:*:*:table/AuroraEvents`
* **Actions:** `PutItem`, `GetItem`, `UpdateItem`, `DeleteItem`, `Query`.

**JSON Policy:**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:PutItem",
                "dynamodb:DeleteItem",
                "dynamodb:GetItem",
                "dynamodb:Query",
                "dynamodb:UpdateItem"
            ],
            "Resource": "arn:aws:dynamodb:*:*:table/AuroraEvents"
        }
    ]
}