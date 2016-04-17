## About

Plugin for [RainbowCrack](http://project-rainbowcrack.com/) to recover your own
Audible activation data (activation_bytes) in an offline manner.

You need to recover or retrieve your "activation_bytes" only once. This single
"activation_bytes" value will work for all your .aax files.

This project is in public domain.

## Usage on Linux

FFmpeg 2.8.1+ is required. Download RainbowCrack for Linux from http://project-rainbowcrack.com/.
Use Wine with Windows binaries in case these Linux executables do not run on
your distribution.

##### Compile the plugin for RainbowCrack

```
make
```

##### Extract SHA1 checksum from the .aax file

```
$ ffprobe test.aax  # extract SHA1 checksum
...
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1dde580] [aax] file checksum == 999a6ab8...
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1dde580] [aax] activation_bytes option is missing!
```

##### Recover "activation_bytes"

```
$ ./rcrack *.rtc -h 999a6ab8...
```

## Usage on Windows

Download FFmpeg from https://ffmpeg.zeranoe.com/builds/.

##### Extract SHA1 checksum from .aax file

```
C:\>ffprobe.exe sample.aax
ffprobe version N-79460-g21acc4d Copyright (c) 2007-2016 the FFmpeg developers
  built with gcc 5.3.0 (GCC)
...
[mov,mp4,m4a,3gp,3g2,mj2 @ 039aae60] [aax] file checksum == 999a6ab8...
[mov,mp4,m4a,3gp,3g2,mj2 @ 039aae60] [aax] activation_bytes option is missing!
```

##### Recover "activation_bytes"

```
C:\tables>run\rcrack.exe *.rtc -h 999a6ab8...
statistics
-------------------------------------------------------
plaintext found:                              1 of 1
total time:                                   13.98 s
...
result
-------------------------------------------------------
999a6ab8...                               xyz   hex:CAFED00D
```

"activation_bytes" is CAFED00D here.

## References

See http://project-rainbowcrack.com/alglib.htm for details.
