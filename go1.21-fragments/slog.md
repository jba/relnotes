## Core library

### +New log/slog package {#slog}

<!--
 https://go.dev/issue/59060, https://go.dev/issue/59141, https://go.dev/issue/59204, https://go.dev/issue/59280,
        https://go.dev/issue/59282, https://go.dev/issue/59339, https://go.dev/issue/59345, https://go.dev/issue/61200,
        CL 477295, CL 484096, CL 486376, CL 486415, CL 487855, CL 508195
-->
The new [log/slog](/pkg/log/slog) package provides structured logging with levels.
Structured logging emits key-value pairs
to enable fast, accurate processing of large amounts of log data.
The package supports integration with popular log analysis tools and services.

### +New testing/slogtest package {#slogtest}

<!-- CL 487895 -->
The new [testing/slogtest](/pkg/testing/slogtest) package can help
to validate [slog.Handler](/pkg/log/slog#Handler) implementations.
