- Tự động đăng kí instance when they come and go
- Request phải được route đến endpoint của instance
- Request phải được load-balanced
- System phải detect được unhealthy instance để tránh 
- Có 2 cách route: 
	 Client-side routing: Client thông qua một service discovery để tìm instance
	 Server-side routing: Tất cả request thông qua reverse proxy để route
Eureka => Kubernetes => 

Why DNS-based is not sufficient?
	A DNS client typically holds on to a working IP address; it does not apply a
	round-robin approach per request.

Eureka là client side-service discovery