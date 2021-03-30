Fluent Bit Windows Development
==============================

[![Build status](https://ci.appveyor.com/api/projects/status/513vwxpalcitl2jo?svg=true)](https://ci.appveyor.com/project/fujimotos/fluent-bit)

Windows port of Fluent Bit is maintained by Fujimoto Seiji <fujimoto@ceptord.net>.

 - The master branch of [ceptord.net/cgit/fluent-bit](http://ceptord.net/cgit/fluent-bit) contains most latest stuffs.  
    - This is the development repository. I mostly grow Windows patches on this repo.
    - After some testing periods, I occasionally ship stable stuffs to [fluent/fluent-bit](https://github.com/fluent/fluent-bit).
    - A breeding-edge Windows build is available on [AppVeyor](https://ci.appveyor.com/api/projects/fujimotos/fluent-bit/artifacts/build/td-agent-bit-1.7.0-win64.zip?job=Platform%3A+x64)
 - For bugs, please create tickets on [fluent/fluent-bit/issues](https://github.com/fluent/fluent-bit/issues)
 - For the list of supported features, see [windows-setup.cmake](http://ceptord.net/cgit/fluent-bit/tree/cmake/windows-setup.cmake)

v1.8 (2021/xx/xx)
-----------------

v1.8 will be the release with HTTP monitoring mechanism.

### Major Features

 - TODO: Port HTTP monitoring feature to Windows.
 - TODO: Port out_kafka to Windows.
 - TODO: Add stacktrace mechanism.
 - TODO: Add Arrow support to out_s3 (all platforms)

### Changed


### Fixed

 - Fix "Missing OpenSSL DLL " issues on v1.7 builds.

v1.7 (2021/02/14)
-----------------

v1.7 is the first Windows release that support "filesystem chunks".

 - Before v1.6, Fluent Bit only support memory chunks. Thus it could lose
   data when it failed to shutdown gracefully (e.g. killed by OOM).

 - With this release, Fluent Bit can persist sending data in disk, which
   makes it more resilient to data loss.

### Major Features

 - New filesystem chunk support (presitent log buffer in disk)
 - Port out_s3 to Windows
 - Port out_kinesis_stream to Windows
 - Port filter_geoip2 to Windows

### Changed

 - Add "String_Inserts" option to in_winlog.
 - Use OpenSSL on the official release build.

### Fixed

 - Fix stalled service issue on Windows Server 2012 (#2296)
 - Fix the default workdir for Windows Service (#2946)
 - Add a fallback mechanism for "ERROR_EVENTLOG_FILE_CHANGED" (#3033)
