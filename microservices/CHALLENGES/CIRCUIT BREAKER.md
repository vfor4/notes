Nếu microserivces dùng blocking synchronous giao tiếp thì khi mà serivce phản hồi lâu, hoặc service bị ngủm thì có thể gây ra chain of failures. 
Vì vậy sinh ra circuit breaker để không nhận thêm request nữa nếu service đang có vấn đề.

**How it works:**
	-  **OPEN** tức là không nhận request nữa. Khi đã mở thì phải fail fast có nghĩa là không có timeout nếu đã detect được  vấn đề của service.
	-  **HALF-OPEN** nhận vào 1 request để xem service đã ổn chưa. Từ đó quyết định trạng thái
	- **CLOSE** chương trình chạy bình thường 