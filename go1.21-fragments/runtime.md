## Runtime

<!-- https://go.dev/issue/7181 -->
When printing very deep stacks, the runtime now prints the first 50
(innermost) frames followed by the bottom 50 (outermost) frames,
rather than just printing the first 100 frames. This makes it easier
to see how deeply recursive stacks started, and is especially
valuable for debugging stack overflows.

<!-- https://go.dev/issue/59960 -->
On Linux platforms that support transparent huge pages, the Go runtime
now manages which parts of the heap may be backed by huge pages more
explicitly. This leads to better utilization of memory: small heaps
should see less memory used (up to 50% in pathological cases) while
large heaps should see fewer broken huge pages for dense parts of the
heap, improving CPU usage and latency by up to 1%.

<!-- https://go.dev/issue/57069, https://go.dev/issue/56966 -->
As a result of runtime-internal garbage collection tuning,
applications may see up to a 40% reduction in application tail latency
and a small decrease in memory use. Some applications may also observe
a small loss in throughput.
The memory use decrease should be proportional to the loss in
throughput, such that the previous release's throughput/memory
tradeoff may be recovered (with little change to latency) by
increasing `GOGC` and/or `GOMEMLIMIT` slightly.

<!-- https://go.dev/issue/51676 -->
Calls from C to Go on threads created in C require some setup to prepare for
Go execution. On Unix platforms, this setup is now preserved across multiple
calls from the same thread. This significantly reduces the overhead of
subsequent C to Go calls from ~1-3 microseconds per call to ~100-200
nanoseconds per call.
