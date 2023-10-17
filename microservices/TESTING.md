
Đối với persistence test, chúng ta chỉ muốn start và tear down database sau khi test xong. Và không muốn phải phụ thuộc nhưng resource khác. Spring cung cấp 2 options:
* @DataMongoTest: khởi động Mongo khi thực hiện test
* @DataJpaTest: khởi động SQL database
Mặc định spring boot rollback lại updates lên database. Để disabled cái rollback này thì dùng
@Transactional(propagation=NOT_SUPPORTED)

## Consumer
* Dùng verifyComplete để test nhưng vẫn lưu kết quả xuống DB
* Vì core services đang nhận event nên:
	1. inject Qualifier("messageProcessor")
	2. truyền event vào method accept của Consumer
	* WebTestClient.BodyContentSpec để kết hợp dùng jsonPath 
## Publisher
* Testing event-drivent microserivices thì khó nhằn, Spring Cloud Stream có hỗ trợ test binder vì vậy không cần bất kì message system nào khi testing cả:
	* 