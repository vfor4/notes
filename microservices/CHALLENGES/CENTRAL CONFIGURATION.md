**Vấn đề:** 
	- Nhiều service, instance thì đồng nghĩa với việc configuration nhiều. Có rất nhiều các config trùng lặp nhau. 
	- Nếu config bị rải đều ra các service thì dev khó có thể hình dung được toàn bộ hệ thống.
	- Việc update trở nên phức tạp
**Giải quyết:**
	- Tạo ra 1 cái config server :> 