Về cơ bản vẫn dùng CallBack hoặc Future của java cũng có thể thực hiện async. Nhưng mà 2 cái này khi thực hiện thì rườm rà, trở nên phức tạp nếu logic phức tạp :)) nên mới có sự suất hiện của Project Reactor (nested callback create call back hell)
Từ lập trình imperative to reactive programing
Nothing happens until you subscribe

Khả năng kết hợp được nhiều async task. gọn gàng dễ đọc dễ thay đổi

![[zimage 20230802213610.png]]

backpressure: subscriber sau khi đăng kí với publisher, thì có thể nhận tất cả signal từ publisher hoặc có thể request số lượng signal

Hot vs Cold

Core Feature

Đối với database relational thì không hỗ trợ reactive nên ta sử dụng Scheduler để làm subscriber.