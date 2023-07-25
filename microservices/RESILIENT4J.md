![[Pasted image 20230724201934.png]]

* if circuit detects too many fail, it will open its circuit
* when the circuit is open, it will perform fail-fast logic. That means it doesn't wait for new fail and will call directly **fallback logic** (return from cache or return immediately error response)
* after a while, the circuit will be half-open, check if new failures are detected or not. and if not it will close otherwise it will still open
## config
* slidingWindowType, slidingWindowSize, failureRateThreshold, ignoreExceptions ...
### time limiter
* use to handle unresponsive services, timeout mechanism
### retry mechanism
* reading information is idempotent, but creating information is not
* maxAttemps(include first call), waitDuration, retryExceptions
*