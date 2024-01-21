- Act like a reverse proxy
- Ẩn đi mấy cái internal service, Expose ra thì phải dùng best practices như là OAuth2, OIDC, JWT tokens và API key ...

	> [!tip]- Một Route được định nghĩa như sau:
	
	> Predicates: điều kiện path sẽ được route
	> Filters: mapping lại path
	> Destination URL: route đến URL
	> ID: Tên của route
	>> [!example]
	> >```java
	> >spring.cloud.gateway.routes:
	>>id: host_route_200
      >>uri: http://httpstat.us
      >>predicates:
      >> - Host=i.feel.lucky:8080
      >> - Path=/headerrouting//**
    >>fiters:
    >> - SetPath=/200
	```

Nếu browser đến i.feel.luck:8080/headerrouting/pourmeone thì sẽ được route đến htpp://httpstat.us/200