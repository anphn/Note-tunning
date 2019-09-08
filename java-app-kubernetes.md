# Tối ưu khởi động container trên kubernetes đối với app java
-----------

* Sử dụng CPU requests, không dùng limit
    
    + Nên request cấu hình CPU 500m cho microservices.
    
    + Nếu 1 pod request 1 CPU, POD có thể sử dụng nhiều hơn tài nguyên được cho phép. Trong trường hợp các pod khác trong cùng node sử dụng tài nguyên cao, thì pod sẽ giảm tài nguyên CPU xuống mức request ban đầu.

* Sử dụng memory limit bằng với memory request
    + Tương tự như CPU pod có thể sử dụng tài nguyên nhiều hơn mà nó request ban đầu, nhưng khác với CPU, Trong trường hợp tài nguyên thấp, nó không thể giảm tài nguyên tương đương với lượng tài nguyên request ban đầu. Cần phải limit để đảm bảo tài nguyên không bị vượt quá.

* Set JVM Heap, e.g. 80 percent of the memory limit
    + Đối với java8 để set JVM Heap sử dụng option -Xmx kèm với câu lệnh khởi động
    Ví dụ:
    
    ```bash
    java", "-Xmx2048m", "-jar", "spring-boot-application.war"
    ```

* Set JVM MaxRAM near to memory limit
    + Đối với java8 để set JVM MaxRAM sử dụng option -XX:MaxRAM kèm với câu lệnh khởi động
    Ví dụ:

    ```bash 
    java", "-Xmx2048m", "-XX:MaxRAM=2048""-jar", "spring-boot-application.war"
    
    ```
