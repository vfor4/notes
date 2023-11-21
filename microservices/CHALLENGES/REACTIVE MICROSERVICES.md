**Vấn Đề**: Khi dùng blocking I/O thì sẽ bị cạn kiệt thread, hoặc là bị treo. Sự sụp đổ của 1 service có nguy cơ kéo theo các service khác. Chain of failures

**Giải quyết:**
- Dùng non-blocking I/O
- Nếu prefer to synchronous programing thì hãy dùng non-blocking của reactive.
- Resilient là service có khả năng response về cho dù service có bị lỗi đi chăng nữa.
- Self-healing là tự phục hồi sau khi bị lỗi hay gì đó.
