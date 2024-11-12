LOCAL_BIN:=$(CURDIR)/bin

install-deps:
	go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.35.1
	go install -mod=mod google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.5.1

get-deps:
	go get -u google.golang.org/grpc
	go get -u google.golang.org/protobuf/cmd/protoc-gen-go
	go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc


generate:
	make generate-chat_server-api

# for windows
generate-chat_server-api:
	if not exist "pkg\chat_server_v1" md "pkg\chat_server_v1"
	protoc --proto_path api\chat_server_v1 \
		--go_out=pkg\chat_server_v1 --go_opt=paths=source_relative \
		--go-grpc_out=pkg\chat_server_v1 --go-grpc_opt=paths=source_relative \
	api\chat_server_v1\chat_server.proto