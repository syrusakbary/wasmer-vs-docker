# Wasmer vs Docker comparison table

This repo tries to analyze the performance of Wasmer packages vs Docker containers in different fields:

* Container/Package size
* Startup time
* Memory usage

## Run the benchmark

You can run the benchmark by doing:

```
make docker                 # This will output the Docker numbers
make docker-alpine          # This will output the Docker (alpine version) numbers
make wasmer                 # This will output the Wasmer numbers
```
