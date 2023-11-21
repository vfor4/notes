* Docker generate raw value
```
docker-compose -f docker-compose.yml config
```
- Chạy jshell với 3 cpu
```
echo 'Runtime.getRuntime().availableProcessors()' | docker run --rm -i eclipse-
temurin:17 jshell -q
```
- Nếu không dùng -Xmx (memory constraint) thì mặc định lấy one-quarter for its heap. Câu lệnh để kiểm tra
```
docker run -it --rm eclipse-temurin:17 java -XX:+PrintFlagsFinal | grep "size_t
MaxHeapSize"
```
- remove all image or container
```
docker rm -f $(docker ps -aq)
```
```
docker rmi -f $(docker images -aq)
```
- start Mongodb CLI
```
docker compose exec mongodb mongosh ––quiet
```
- start MySQL CLI
```
docker compose exec mysql mysql -uuser -p review-db
```
