# Diagnostic Report

<!--introduced_in=v11.8.0-->
<!-- type=misc -->

> Stability: 1 - Experimental

<!-- name=report -->

Delivers a JSON-formatted diagnostic summary, written to a file.

The report is intended for development, test and production use, to capture
and preserve information for problem determination. It includes JavaScript
and native stack traces, heap statistics, platform information, resource
usage etc. With the report option enabled, diagnostic reports can be triggered
on unhandled exceptions, fatal errors and user signals, in addition to
triggering programmatically through API calls.

A complete example report that was generated on an uncaught exception
is provided below for reference.

```json
{
  "header": {
    "event": "exception",
    "location": "OnUncaughtException",
    "filename": "report.20181221.005011.8974.001.json",
    "dumpEventTime": "2018-12-21T00:50:11Z",
    "dumpEventTimeStamp": "1545371411331",
    "processId": 8974,
    "commandLine": [
      "/home/nodeuser/project/node/out/Release/node",
      "--experimental-report",
      "--diagnostic-report-uncaught-exception",
      "/home/nodeuser/project/node/test/node-report/test-exception.js",
      "child"
    ],
    "nodejsVersion": "v12.0.0-pre",
    "glibcVersionRuntime": "2.17",
    "glibcVersionCompiler": "2.17",
    "wordSize": "64 bit",
    "arch": "x64",
    "platform": "linux",
    "componentVersions": {
      "node": "12.0.0-pre",
      "v8": "7.1.302.28-node.5",
      "uv": "1.24.1",
      "zlib": "1.2.11",
      "ares": "1.15.0",
      "modules": "68",
      "nghttp2": "1.34.0",
      "napi": "3",
      "llhttp": "1.0.1",
      "http_parser": "2.8.0",
      "openssl": "1.1.0j"
    },
    "release": {
      "name": "node"
    },
    "osVersion": "Linux 3.10.0-862.el7.x86_64 #1 SMP Wed Mar 21 18:14:51 EDT 2018",
    "machine": "test_machine x86_64"
  },
  "javascriptStack": {
    "message": "Error: *** test-exception.js: throwing uncaught Error",
    "stack": [
      "at myException (/home/nodeuser/project/node/test/node-report/test-exception.js:9:11)",
      "at Object.<anonymous> (/home/nodeuser/project/node/test/node-report/test-exception.js:12:3)",
      "at Module._compile (internal/modules/cjs/loader.js:718:30)",
      "at Object.Module._extensions..js (internal/modules/cjs/loader.js:729:10)",
      "at Module.load (internal/modules/cjs/loader.js:617:32)",
      "at tryModuleLoad (internal/modules/cjs/loader.js:560:12)",
      "at Function.Module._load (internal/modules/cjs/loader.js:552:3)",
      "at Function.Module.runMain (internal/modules/cjs/loader.js:771:12)",
      "at executeUserCode (internal/bootstrap/node.js:332:15)"
    ]
  },
  "nativeStack": [
    " [pc=0xa7ef87]  [/home/nodeuser/project/node/out/Release/node]",
    " [pc=0xa81adb] report::TriggerNodeReport(v8::Isolate*, node::Environment*, char const*, char const*, std::string, v8::Local<v8::String>) [/home/nodeuser/project/node/out/Release/node]",
    " [pc=0xa834f2] report::OnUncaughtException(v8::FunctionCallbackInfo<v8::Value> const&) [/home/nodeuser/project/node/out/Release/node]",
    " [pc=0xbe6b78]  [/home/nodeuser/project/node/out/Release/node]",
    " [pc=0xbe7596] v8::internal::Builtin_HandleApiCall(int, v8::internal::Object**, v8::internal::Isolate*) [/home/nodeuser/project/node/out/Release/node]",
    " [pc=0x1930cae]  [/home/nodeuser/project/node/out/Release/node]"
  ],
  "javascriptHeap": {
    "totalMemory": 6127616,
    "totalCommittedMemory": 4357352,
    "usedMemory": 3221136,
    "availableMemory": 1521370240,
    "memoryLimit": 1526909922,
    "heapSpaces": {
      "read_only_space": {
        "memorySize": 524288,
        "committedMemory": 39208,
        "capacity": 515584,
        "used": 30504,
        "available": 485080
      },
      "new_space": {
        "memorySize": 2097152,
        "committedMemory": 2019312,
        "capacity": 1031168,
        "used": 985496,
        "available": 45672
      },
      "old_space": {
        "memorySize": 2273280,
        "committedMemory": 1769008,
        "capacity": 1974640,
        "used": 1725488,
        "available": 249152
      },
      "code_space": {
        "memorySize": 696320,
        "committedMemory": 184896,
        "capacity": 152128,
        "used": 152128,
        "available": 0
      },
      "map_space": {
        "memorySize": 536576,
        "committedMemory": 344928,
        "capacity": 327520,
        "used": 327520,
        "available": 0
      },
      "large_object_space": {
        "memorySize": 0,
        "committedMemory": 0,
        "capacity": 1520590336,
        "used": 0,
        "available": 1520590336
      },
      "new_large_object_space": {
        "memorySize": 0,
        "committedMemory": 0,
        "capacity": 0,
        "used": 0,
        "available": 0
      }
    }
  },
  "resourceUsage": {
    "userCpuSeconds": 0.069595,
    "kernelCpuSeconds": 0.019163,
    "cpuConsumptionPercent": 0.000000,
    "maxRss": 18079744,
    "pageFaults": {
      "IORequired": 0,
      "IONotRequired": 4610
    },
    "fsActivity": {
      "reads": 0,
      "writes": 0
    }
  },
  "uvthreadResourceUsage": {
    "userCpuSeconds": 0.068457,
    "kernelCpuSeconds": 0.019127,
    "cpuConsumptionPercent": 0.000000,
    "fsActivity": {
      "reads": 0,
      "writes": 0
    }
  },
  "libuv": [
    {
      "type": "async",
      "is_active": true,
      "is_referenced": false,
      "address": "68090592",
      "details": ""
    },
    {
      "type": "timer",
      "is_active": false,
      "is_referenced": false,
      "address": "140723513949920",
      "details": "repeat: 0, timeout expired: 18075165916 ms ago"
    },
    {
      "type": "check",
      "is_active": true,
      "is_referenced": false,
      "address": "140723513950072",
      "details": ""
    },
    {
      "type": "idle",
      "is_active": false,
      "is_referenced": true,
      "address": "140723513950192",
      "details": ""
    },
    {
      "type": "prepare",
      "is_active": false,
      "is_referenced": false,
      "address": "140723513950312",
      "details": ""
    },
    {
      "type": "check",
      "is_active": false,
      "is_referenced": false,
      "address": "140723513950432",
      "details": ""
    },
    {
      "type": "async",
      "is_active": true,
      "is_referenced": false,
      "address": "39353856",
      "details": ""
    }
  ],
  "environmentVariables": {
    "REMOTEHOST": "REMOVED",
    "MANPATH": "/opt/rh/devtoolset-3/root/usr/share/man:",
    "XDG_SESSION_ID": "66126",
    "HOSTNAME": "test_machine",
    "HOST": "test_machine",
    "TERM": "xterm-256color",
    "SHELL": "/bin/csh",
    "SSH_CLIENT": "REMOVED",
    "PERL5LIB": "/opt/rh/devtoolset-3/root//usr/lib64/perl5/vendor_perl:/opt/rh/devtoolset-3/root/usr/lib/perl5:/opt/rh/devtoolset-3/root//usr/share/perl5/vendor_perl",
    "OLDPWD": "/home/nodeuser/project/node/src",
    "JAVACONFDIRS": "/opt/rh/devtoolset-3/root/etc/java:/etc/java",
    "SSH_TTY": "/dev/pts/0",
    "PCP_DIR": "/opt/rh/devtoolset-3/root",
    "GROUP": "normaluser",
    "USER": "nodeuser",
    "LD_LIBRARY_PATH": "/opt/rh/devtoolset-3/root/usr/lib64:/opt/rh/devtoolset-3/root/usr/lib",
    "HOSTTYPE": "x86_64-linux",
    "XDG_CONFIG_DIRS": "/opt/rh/devtoolset-3/root/etc/xdg:/etc/xdg",
    "MAIL": "/var/spool/mail/nodeuser",
    "PATH": "/home/nodeuser/project/node:/opt/rh/devtoolset-3/root/usr/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin",
    "PWD": "/home/nodeuser/project/node",
    "LANG": "en_US.UTF-8",
    "PS1": "\\u@\\h : \\[\\e[31m\\]\\w\\[\\e[m\\] >  ",
    "SHLVL": "2",
    "HOME": "/home/nodeuser",
    "OSTYPE": "linux",
    "VENDOR": "unknown",
    "PYTHONPATH": "/opt/rh/devtoolset-3/root/usr/lib64/python2.7/site-packages:/opt/rh/devtoolset-3/root/usr/lib/python2.7/site-packages",
    "MACHTYPE": "x86_64",
    "LOGNAME": "nodeuser",
    "XDG_DATA_DIRS": "/opt/rh/devtoolset-3/root/usr/share:/usr/local/share:/usr/share",
    "LESSOPEN": "||/usr/bin/lesspipe.sh %s",
    "INFOPATH": "/opt/rh/devtoolset-3/root/usr/share/info",
    "XDG_RUNTIME_DIR": "/run/user/50141",
    "_": "./node"
  },
  "userLimits": {
    "core_file_size_blocks": {
      "soft": "",
      "hard": "unlimited"
    },
    "data_seg_size_kbytes": {
      "soft": "unlimited",
      "hard": "unlimited"
    },
    "file_size_blocks": {
      "soft": "unlimited",
      "hard": "unlimited"
    },
    "max_locked_memory_bytes": {
      "soft": "unlimited",
      "hard": 65536
    },
    "max_memory_size_kbytes": {
      "soft": "unlimited",
      "hard": "unlimited"
    },
    "open_files": {
      "soft": "unlimited",
      "hard": 4096
    },
    "stack_size_bytes": {
      "soft": "unlimited",
      "hard": "unlimited"
    },
    "cpu_time_seconds": {
      "soft": "unlimited",
      "hard": "unlimited"
    },
    "max_user_processes": {
      "soft": "unlimited",
      "hard": 4127290
    },
    "virtual_memory_kbytes": {
      "soft": "unlimited",
      "hard": "unlimited"
    }
  },
  "sharedObjects": [
    "/lib64/libdl.so.2",
    "/lib64/librt.so.1",
    "/lib64/libstdc++.so.6",
    "/lib64/libm.so.6",
    "/lib64/libgcc_s.so.1",
    "/lib64/libpthread.so.0",
    "/lib64/libc.so.6",
    "/lib64/ld-linux-x86-64.so.2"
  ]
}
```

## Usage

```bash
node --experimental-report --diagnostic-report-uncaught-exception \
  --diagnostic-report-on-signal --diagnostic-report-on-fatalerror app.js
```

* `--experimental-report` Enables the diagnostic report feature.
 In the absence of this flag, use of all other related options will result in
 an error.

* `--diagnostic-report-uncaught-exception` Enables report to be generated on
un-caught exceptions. Useful when inspecting JavaScript stack in conjunction
with native stack and other runtime environment data.

* `--diagnostic-report-on-signal` Enables report to be generated upon receiving
the specified (or predefined) signal to the running Node.js process. (See below
on how to modify the signal that triggers the report.) Default signal is `SIGUSR2`.
Useful when a report needs to be triggered from another program.
Application monitors may leverage this feature to collect report at regular
intervals and plot rich set of internal runtime data to their views.

Signal based report generation is not supported in Windows.

Under normal circumstances, there is no need to modify the report triggering
signal. However, if `SIGUSR2` is already used for other purposes, then this
flag helps to change the signal for report generation and preserve the original
meaning of `SIGUSR2` for the said purposes.

* `--diagnostic-report-on-fatalerror` Enables the report to be triggered on
fatal errors (internal errors within the Node.js runtime, such as out of memory)
that leads to termination of the application. Useful to inspect various
diagnostic data elements such as heap, stack, event loop state, resource
consumption etc. to reason about the fatal error.

* `--diagnostic-report-directory` Location at which the report will be
generated.

* `--diagnostic-report-filename` Name of the file to which the report will be
written.

* `--diagnostic-report-signal` Sets or resets the signal for report generation
(not supported on Windows). Default signal is `SIGUSR2`.

* `--diagnostic-report-verbose` Flag that enables additional information to be
printed during report generation.

A report can also be triggered via an API call from a JavaScript application:

```js
process.report.triggerReport();
```

This function takes an optional additional argument `filename`, which is
the name of a file into which the report is written.

```js
process.report.triggerReport('./foo.json');
```

This function takes an optional additional argument `err` - an `Error` object
that will be used as the context for the JavaScript stack printed in the report.
When using report to handle errors in a callback or an exception handler, this
allows the report to include the location of the original error as well
as where it was handled.

```js
try {
  process.chdir('/non-existent-path');
} catch (err) {
  process.report.triggerReport(err);
}
// Any other code
```

If both filename and error object are passed to `triggerReport()` the
error object must be the second parameter.

```js
try {
  process.chdir('/non-existent-path');
} catch (err) {
  process.report.triggerReport(filename, err);
}
// Any other code
```

The content of the diagnostic report can be returned as a JSON-compatible object
via an API call from a JavaScript application:

```js
const report = process.report.getReport();
console.log(report);
```

This function takes an optional additional argument `err` - an `Error` object
that will be used as the context for the JavaScript stack printed in the report.

```js
const report = process.report.getReport(new Error('custom error'));
console.log(report);
```

The API versions are useful when inspecting the runtime state from within
the application, in expectation of self-adjusting the resource consumption,
load balancing, monitoring etc.

The content of the report consists of a header section containing the event
type, date, time, PID and Node.js version, sections containing JavaScript and
native stack traces, a section containing V8 heap information, a section
containing `libuv` handle information and an OS platform information section
showing CPU and memory usage and system limits. An example report can be
triggered using the Node.js REPL:

```raw
$ node
> process.report.triggerReport();
Writing Node.js report to file: report.20181126.091102.8480.001.json
Node.js report completed
>
```

When a report is triggered, start and end messages are issued to stderr
and the filename of the report is returned to the caller. The default filename
includes the date, time, PID and a sequence number. The sequence number helps
in associating the report dump with the runtime state if generated multiple
times for the same Node.js process.

## Configuration

Additional runtime configuration that influences the report generation
constraints are available using `setDiagnosticReportOptions()` API.

```js
process.report.setDiagnosticReportOptions({
  events: ['exception', 'fatalerror', 'signal'],
  signal: 'SIGUSR2',
  filename: 'myreport.json',
  path: '/home/nodeuser',
  verbose: true
});
```

The `events` array contains one or more of the report triggering options.
The only valid entries are `'exception'`, `'fatalerror'` and `'signal'`.
By default, a report is not produced on any of these events.

`signal` specifies the POSIX signal identifier that will be used
to intercept external triggers for report generation. Defaults to
`'SIGUSR2'`.

`filename` specifies the name of the output file in the file system.
Special meaning is attached to `stdout` and `stderr`. Usage of these
will result in report being written to the associated standard streams.
In such cases when standard streams are used, value in `'path'` is ignored.
URLs are not supported. Defaults to a composite filename that contains
timestamp, PID and sequence number.

`path` specifies the filesystem directory where the report will be written to.
URLs are not supported. Defaults to the current working directory of the
Node.js process.

`verbose` specifies whether to print additional verbose messages
pertinent to the report generation. Defaults to `false`.

```js
// Trigger report only on uncaught exceptions.
process.report.setDiagnosticReportOptions({ events: ['exception'] });

// Trigger report for both internal errors as well as external signal.
process.report.setDiagnosticReportOptions({ events: ['fatalerror', 'signal'] });

// Change the default signal to `SIGQUIT` and enable it.
process.report.setDiagnosticReportOptions(
  { events: ['signal'], signal: 'SIGQUIT' });
```

Configuration on module initialization is also available via
environment variables:

```bash
NODE_OPTIONS="--experimental-report --diagnostic-report-uncaught-exception \
  --diagnostic-report-on-fatalerror --diagnostic-report-on-signal \
  --diagnostic-report-signal=SIGUSR2  --diagnostic-report-filename=./report.json \
  --diagnostic-report-directory=/home/nodeuser --diagnostic-report-verbose"
```

Specific API documentation can be found under
[`process API documentation`][] section.

[`process API documentation`]: process.html