#!/bin/bash

# Include the script
. "$(pwd)/bench.in"

# Init environment
bench_init 1 0

# Add benchmarks
bench_add "Sleepy" 10 "sleep 0.1"
bench_add "" 10 "date +%s"
bench_add "" 10 "date +%N"

# Run benchmarks
bench_run
