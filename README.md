# bench-bash

A minimal benchmarking framework contained in a single bash script.

## Dependencies

* `bash`
* `bc`
* `awk`
* `sort`

## Api

To use `bench-bash` you need to source [`bench.in`](bench.in).
You can do this by using `.` or `source`.

```
. "path/.../bench.in"
# or
source "path/.../bench.in"
```

### bench_init

Initialize/reset benchmarking environment.
Call this function instead of manually manipulating `BENCH_*` variables.

```
bench_init use_color default_log
           |         |
           |         `-- Log the result of benchmarks to file
           |
           `-- Use colors in output. Always disabled if stdout is not a terminal
```

### bench_add

Add a benchmark to the benchmarking environment.

```
bench_add name runs cmd [inf] [outf] [errf]
          |    |    |   |     |      |
          |    |    |   |     `-- File in which the benchmark stdout/stderr is logged
          |    |    |   `-- File to pipe in the stdin of the benchmark. Default to nothing
          |    |    `-- Command to run for the benchmark
          |    `-- Number of runs for the benchmark
          `-- Name of the benchmark. If left blank the number of the benchmark is used
```

### bench_run

Run benchmarks in the benchmarking environment.

```
bench_run
```

## Example

```
$ ./test
Benchmark Sleepy: `sleep 0.1`
  Real time:
    Range: 0.101 s max ... 0.101 s min
    Mean: 0.101 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  User time:
    Range: 0.001 s max ... 0.000 s min
    Mean: 0.0009 s ± 0 s
    Deviation: 0.0003 s
    Error: 0 s
  System time:
    Range: 0.000 s max ... 0.000 s min
    Mean: 0 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  Runs: 0 errors, 10 successes over 10 runs

Benchmark #2: `date +%s`
  Real time:
    Range: 0.001 s max ... 0.001 s min
    Mean: 0.001 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  User time:
    Range: 0.001 s max ... 0.000 s min
    Mean: 0.0003 s ± 0.0001 s
    Deviation: 0.000458258 s
    Error: 0.0001 s
  System time:
    Range: 0.000 s max ... 0.000 s min
    Mean: 0 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  Runs: 0 errors, 10 successes over 10 runs

Benchmark #3: `date +%N`
  Real time:
    Range: 0.001 s max ... 0.001 s min
    Mean: 0.001 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  User time:
    Range: 0.001 s max ... 0.000 s min
    Mean: 0.0007 s ± 0.0001 s
    Deviation: 0.000458258 s
    Error: 0.0001 s
  System time:
    Range: 0.000 s max ... 0.000 s min
    Mean: 0 s ± 0 s
    Deviation: 0 s
    Error: 0 s
  Runs: 0 errors, 10 successes over 10 runs

Summary:
  Fastest benchmark: #3, real time mean 0.001 s ± 0 s
  Slowest benchmark: Sleepy, real time mean 0.101 s ± 0 s
  Total time:
    Elapsed since run: 1 s
    Elapsed since init: 1 s
```

## License

Copyright (C) 2021 @bynect

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
