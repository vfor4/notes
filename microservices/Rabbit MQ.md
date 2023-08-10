Là một message broker bao gồm:
* Producer: một program mà gửi message
* Queue: giống như là hòm thư, message chỉ có thể được chứa bên trong queue 
* Consumer: một program mà nhận message

### Spring cloud stream (event-driven microservices)
* Bindings: cầu nối giữa giữa app và binder ( áp sẽ gửi message qua cầu này đến binder)
	-Có 2 loại bindings:
	 > input như sau: functionName -in- index
	 >    output như sau: functionName -out- index 
	
	\-Ví dụ: Map input của function uppercase với queue có tên là myQueue
	```java
	spring.cloud.stream.bindings.uppercase-in-0.destination=myQueue
	```
	
* Binder (message broker): rabbitmq hay kafka
* Message: 
### Challenges
1. Comsumers group
	Nếu chúng ta scale up hệ thống lên 2 instances của 1 service thì khi xử lý message cả 2 đều sẽ đồng thời xử lý cùng 1 message. Như vậy là không được. 
	Giải quyết vấn đề này bằng cách cấu hình comsumer group
2. Retries và dead-letter queues
	- Khi consumer xử lý message bị lỗi thì retry lại
	- Sau khi retry mà khi xử dụng message vẫn gây ra lỗi thì gửi nó đến DLQ, từ queue này mình có thể re-process hoặc auditing hoặc hòa giải :))
3. Order and parittions
	- Khi cần dữ liệu liên quan đến nhau phải được xử lý cùng nhau và theo thứ tự được gửi đi
	- Chỉ định key cho mỗi message, những message nào có cùng key thì sẽ nằm cùng 1 partition![[zimage 20230807192753.png|{width=50%}]]
	- Cần phải config ở cả publisher và consumer
# THỰC HIỆN
Để có thể consume event, thực hiện các bước sau:
* Khai báo message processor để nhận event, sau khi nhận được event rồi thì sẽ tiến hành gọi đến các hàm delete, create ở persistence layer
* Các service được gọi phải đang dùng reactive
* Config properties cho các consumer