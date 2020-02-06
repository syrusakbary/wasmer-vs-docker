docker:
	# Docker container size: 1.72GB
	# Running time: ~614ms
	# Memory peak: 22960

	# Prepare the container
	docker build -t my-rust-app .

	# Get the size of the container
	docker images | grep my-rust-app

	# Time it!
	time docker run -it --rm --name my-running-app my-rust-app

	# Analyze memory usage
	../memusg.sh docker run -it --rm --name my-running-app my-rust-app

# Alpine not supported here because of musl dependency issues on the Rust Crate

# docker-alpine:
# 	# Docker container size: 83.5MB
# 	# Running time: ~580ms
# 	# Memory peak: 23000

# 	# Prepare the container
# 	docker build -f Dockerfile.alpine -t my-rust-app-alpine .

# 	# Get the size of the container
# 	docker images | grep my-rust-app-alpine

# 	# Time it!
# 	time docker run -it --rm --name my-running-app my-rust-app-alpine

# 	# Analyze memory usage
# 	../memusg.sh docker run -it --rm --name my-running-app my-rust-app-alpine


wasmer:
	# Wasmer package size:  340 KB (from https://wapm.io/package/cowsay)
	# Running time: ~30ms
	# Memory usage: 320

	# Package size retrieved from here: https://wapm.io/package/php

	# Prepare the container (precompile). Note: it might take a minute
	wasmer run cowsay/target/wasm32-wasi/release/cowsay.wasm -- -V

	# Time it!
	time wasmer run cowsay/target/wasm32-wasi/release/cowsay.wasm "Hello World"

	# Analyze memory usage
	../memusg.sh wasmer run cowsay/target/wasm32-wasi/release/cowsay.wasm "Hello World"
