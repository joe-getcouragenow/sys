SHARED_FSPATH=./../../shared
BOILERPLATE_FSPATH=$(SHARED_FSPATH)/boilerplate

include $(BOILERPLATE_FSPATH)/help.mk
include $(BOILERPLATE_FSPATH)/os.mk
include $(BOILERPLATE_FSPATH)/gitr.mk
include $(BOILERPLATE_FSPATH)/tool.mk
include $(BOILERPLATE_FSPATH)/flu.mk
include $(BOILERPLATE_FSPATH)/go.mk

override FLU_SAMPLE_NAME =example
override FLU_LIB_NAME =client
override FLU_SAMPLE_FSPATH = $(PWD)/main/client

BIN_FOLDER=./bin-all
EXAMPLE_SERVER_BIN=$(BIN_FOLDER)/server
EXAMPLE_CLI_BIN=$(BIN_FOLDER)/cli

this-all: this-print this-gen this-build this-print-end

## Print all settings
this-print:
	@echo
	@echo "-- SYS:SYS-CORE: start --"
	@echo EXAMPLE_SERVER_BIN: $(EXAMPLE_SERVER_BIN)
	@echo EXAMPLE_SDK_BIN: $(EXAMPLE_CLI_BIN)
	@echo

this-print-end:
	@echo
	@echo "-- SYS:SYS-CORE: end --"
	@echo
	@echo



## This builds everything
this-build: this-build-clean
	@echo "Building example golang binaries (CLI and Server)"
	mkdir -p $(EXAMPLE_SERVER_BIN)
	mkdir -p $(EXAMPLE_CLI_BIN)

	go build -v -o $(EXAMPLE_SERVER_BIN) ./example/server/go/main.go
	go build -v -o $(EXAMPLE_CLI_BIN) ./example/cli/go/main.go

this-build-clean:
	rm -rf $(BIN_FOLDER)

this-gen:this-gen-clean
	# Go
	@go generate
this-gen-clean:
	# NONE

## Build and Run Server Example (Temporary until structure/stack is fixed)
this-ex-server-run:
	@echo Running Example Server
	cd ./bin-all/server && ./main

this-ex-ui-run:
	@echo Running grpc-ui
	@grpcui -plaintext localhost:8888
