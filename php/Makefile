docker:
	# Docker container size: 410MB
	# Running time: ~620ms
	# Memory peak: 23000

	# Prepare the container
	docker build -t my-php-app .

	# Get the size of the container
	docker images | grep my-php-app

	# Time it!
	time docker run -it --rm --name my-running-app my-php-app

	# Analyze memory usage
	./memusg.sh docker run -it --rm --name my-running-app my-php-app

docker-alpine:
	# Docker container size: 83.5MB
	# Running time: ~580ms
	# Memory peak: 23000

	# Prepare the container
	docker build -f Dockerfile.alpine -t my-php-app-alpine .

	# Get the size of the container
	docker images | grep my-php-app-alpine

	# Time it!
	time docker run -it --rm --name my-running-app my-php-app-alpine

	# Analyze memory usage
	./memusg.sh docker run -it --rm --name my-running-app my-php-app-alpine

wasmer:
	# Wasmer package size:  1.68 MB
	# Running time: ~90ms
	# Memory usage: 320

	# Package size retrieved from here: https://wapm.io/package/php

	# Prepare the container (precompile). Note: it might take a minute
	wasmer run wapm_packages/_/php@0.1.1/php.wasm -- example.php ""

	# Time it!
	time wasmer run wapm_packages/_/php@0.1.1/php.wasm -- example.php "Hello World"

	# Analyze memory usage
	./memusg.sh wasmer run wapm_packages/_/php@0.1.1/php.wasm -- example.php "Hello World"
