docker:
	# Docker container size: 1.67GB
	# Running time: ~350ms
	# Memory peak: 24676

	# Prepare the container
	docker build -t my-rust-app .

	# Get the size of the container
	docker images | grep my-rust-app

	@ docker create --net=host --pid=host --name my-running-app-1 my-rust-app >/dev/null
	# Time it!
	time docker start -i my-running-app-1
	@ docker rm -f my-running-app-1 >/dev/null

	@ docker create --net=host --pid=host --name my-running-app-2 my-rust-app >/dev/null
	# Analyze memory usage
	../memusg.sh docker start -i my-running-app-2
	@ docker rm -f my-running-app-2 >/dev/null

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
	wasmer run wapm_packages/_/cowsay@0.2.0/target/wasm32-wasi/release/cowsay.wasm -- -V

	# Time it!
	time wasmer run wapm_packages/_/cowsay@0.2.0/target/wasm32-wasi/release/cowsay.wasm "Hello World"

	# Analyze memory usage
	../memusg.sh wasmer run wapm_packages/_/cowsay@0.2.0/target/wasm32-wasi/release/cowsay.wasm "Hello World"
