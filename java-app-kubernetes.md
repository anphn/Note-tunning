# Tối ưu khởi động container trên kubernetes đối với app java
-----------

* Use CPU requests, but no limit
    
    + Nên request cấu hình CPU 500m cho microservices.
    
    + Nếu 1 pod request 1 CPU, POD có thể sử dụng nhiều hơn tài nguyên được cho phép. Trong trường hợp các pod khác trong cùng node sử dụng tài nguyên cao, thì pod sẽ giảm tài nguyên CPU xuống mức request ban đầu.

* Use memory limit equal to memory request
    + Tương tự như CPU pod có thể sử dụng tài nguyên nhiều hơn mà nó request ban đầu, nhưng khác với CPU, Trong trường hợp tài nguyên thấp, nó không thể giảm tài nguyên tương đương với lượng tài nguyên request ban đầu. Cần phải limit để đảm bảo tài nguyên không bị vượt quá.

* Set JVM Heap, e.g. 80 percent of the memory limit
* Set JVM MaxRAM near to memory limit
