Tuyệt vời\! Bạn đã có một hệ thống đăng nhập xịn sò. Tuy nhiên, hiện tại khi người dùng đăng nhập bằng Clerk trên Web, **Database PostgreSQL của bạn vẫn chưa biết người đó là ai** (chưa có dữ liệu trong bảng `User`).

Để giải quyết vấn đề này, chúng ta sẽ thực hiện **Task 3: Dùng Webhook để đồng bộ tài khoản từ Clerk về Database**.

Cách hoạt động: Khi có ai đó đăng ký mới trên Web, Clerk sẽ tự động "gọi điện" (gửi một request Webhook) cho Backend NestJS của bạn, mang theo thông tin user để lưu vào DB.

Hãy làm theo các bước sau nhé:

### Bước 1: Đổi cổng (port) cho Backend NestJS

Vì Frontend Next.js của bạn đang chạy ở cổng `3000`, chúng ta cần cho Backend chạy ở cổng `3001` để tránh xung đột.

1.  Mở file `apps/api/src/main.ts`.
2.  Sửa lại thành như sau (chú ý thêm dòng `app.enableCors()` để sau này Web có thể gọi API):

<!-- end list
