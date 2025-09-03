# What is JMH?

JMH ([Java Microbenchmark Harness](https://openjdk.org/projects/code-tools/jmh/))
 is the official toolkit from the OpenJDK team for writing reliable microbenchmarks on the JVM.

Writing System.nanoTime() loops is misleading because the JVM JIT compiler can inline methods, remove dead code, 
or apply optimizations that distort results. JMH takes care of this by:
- running warmup iterations, so the JIT has time to optimize the code before measurement;
- preventing dead code elimination with special “blackholes”;
- running benchmarks in forked JVMs to isolate measurements;
- reporting results with confidence intervals and multiple measurement modes.

Key annotations:
- `@Benchmark` — method to measure.
- `@Warmup` — warmup iterations before measurement.
- `@Measurement` — how long and how many iterations to measure.
- `@Fork` — how many separate JVM processes to run.
- `@State` — shared input/state for a benchmark.

Modes:
- `Throughput` (ops/time)
- `AverageTime` (time/op)
- `SampleTime` (distribution)

Example result:
```text
Benchmark              Mode  Cnt     Score    Error  Units
MyBench.testMethod    thrpt    5  52414.810 ± 346.029 ops/ms
```
