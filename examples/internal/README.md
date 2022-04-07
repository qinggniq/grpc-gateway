# 网关服务示例
调用链路为 client -[http]-> gateway -[grpc]-> server
## 编译
```shell
$ go build -o bin/example-server github.com/grpc-ecosystem/grpc-gateway/v2/examples/internal/cmd/example-grpc-server # 编译 server
$ go build -o bin/example-gw github.com/grpc-ecosystem/grpc-gateway/v2/examples/internal/cmd/example-gateway-server # 编译 gateway
```
## 运行
### 运行 server
server默认监听9090端口。
```shell
$ ./bin/example-server --logtostderr 
```
### 运行 gateway 
gateway默认监听8080端口
```shell
$ ./bin/example-gw --logtostderr --openapi_dir ../proto/examplepb
```
## 验证
```shell
$ curl http://localhost:8080/v1/example/echo/foo/123
```