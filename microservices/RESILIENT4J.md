![[zimage 20230724201934.png]]

* if circuit detects too many fail, it will open its circuit
* when the circuit is open, it will perform fail-fast logic. That means it doesn't wait for new fail and will call directly **fallback logic** (return from cache or return immediately error response)
* after a while, the circuit will be half-open, check if new failures are detected or not. and if not it will close otherwise it will still open
## config
* slidingWindowType, slidingWindowSize, failureRateThreshold, ignoreExceptions ...
* everything here: https://resilience4j.readme.io/docs/circuitbreaker#create-and-configure-a-circuitbreaker
### time limiter
* use to handle unresponsive services, timeout mechanism. Là property để set timeout cho một request
### retry mechanism
* reading information is idempotent, but creating information is not
* Cẩn thận khi làm retry, mọi api khi retry đều phải mang tính idempotent ( kết quả là không đổi dù có gọi bao nhiêu lần trên cùng 1 request)
* maxAttemps(include first call), waitDuration, retryExceptions
* https://resilience4j.readme.io/docs/retry#create-and-configure-retry
### useful actuator endpoints
- actuator/retryevents
-Khi breaker open thì lúc request gửi đến sẽ throw ra CallNotPermittedException