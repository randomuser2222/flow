.PHONY: cleanup
cleanup:
	rm -rf ./go/flow/access ./go/flow/entities
	rm -rf ./js
	mkdir ./js

.PHONY: generate
generate: cleanup generate-js

.PHONY: generate-go
generate-go:
	prototool generate

.PHONY: generate-js
generate-js:
	protoc \
	--plugin="protoc-gen-ts=./node_modules/.bin/protoc-gen-ts" \
	--js_out="import_style=commonjs,binary:js" \
	--ts_out="service=grpc-web:js" \
	-I ./ \
	flow/**/*.proto;
