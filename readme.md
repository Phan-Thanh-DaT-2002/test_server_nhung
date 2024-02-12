## Hướng dẫn khai báo ORM

Mô tả: Việc thiết kế call API theo các package trong Database.

Khi khai báo /orm

Nếu sử dụng method GET

Thì không sử dụng body khi gọi

Nếu sử dụng method POST, PUT, DELETE thì nên sử dụng theo request body

## Tính năng của project:

### Menu:

Đã cấu hình được N cấp, trong đó có trang /dashboard không nên xóa, nó sẽ trả về trang chủ của trang web.

CHECK Token Expired khi reload menu (F5) hoặc click vào menu của hệ thống, đều được check Expired Time của TOKEN.

Khi TOKEN không hợp lệ thì sẽ đẩy ra ngoài trang Login, yêu cầu người dùng login lại.

## Hướng dẫn build, running Eruka-Server, Zuuli-APIGW

Window: Maven + Java 8.

Yêu cầu: Cài đặt Maven trong đường dẫn Path của máy tính.

### Các bước chạy:

Bước 0: Mở 3 cái termail: 

(Eureka Server) + (Zuuly API) + (Core Service)

Bước 1: cd ra thư mục gốc của project: neo-themes\zuul-apigateway, neo-themes\eureka-server

Bước 2: Clean + build project: mvn clean install

```
Project tự động clean (xóa đi code cũ) + build (tạo file xxx.jar mới).
```

Bước 3: cd vào thư mục /target (cd target) và chạy lệnh

```
+ Eureka-Server:

java -jar -Xmx1024M -Xms64M eureka-server-0.0.1-SNAPSHOT.jar

+ Zuuly API:
java -jar -Xmx1024M -Xms64M api-gateway-0.0.1-SNAPSHOT.jar


```

## Flow dữ liệu qua các tầng

Mô hình: Controller <--DTO--> Service <--Model/mapper--> Repository <--Entity--> Database

Trong đó:

Entity: Object ánh xác các trường trong Database

DTO: Data Transfer Object - tầng chuyển đổi dữ liệu ra ngoài Client/Controller

Mapper: Tầng convert dữ liệu từ Entity thành DTO

Request: Tầng chứa các Object request cho Controller

Giải thích scope trong các tầng:

Entity > DTO > Request

## Hướng dẫn deploy module (EurekaServer, Zuuly APIGW, CoreService) lên Server CentOS7

### Môi trường cân chuẩn bị

Java 8 (Đã set JAVA_HOME)

Thông kết nối Database version 12C

### Build ứng dụng

command line: mvn clean install để build ứng dụng với các module maven.

(... tài liệu hướng dẫn triển khai module)

WARNING...: Không sử dụng dependency devtool cho môi trường deploy lên Server

