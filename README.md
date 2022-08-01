# Usage
`x262.exe --fullhelp`  
`x262.exe --crf 1.0 --vbv-maxrate 9500 --vbv-bufsize 1835 --keyint 12 --sar 16:9 --fps 25 --bframes 0 --dc 10 --mpeg2 -o output.m2v input.y4m`

# FFmpeg import
`ffmpeg -i input.mkv -f yuv4mpegpipe - | x262 --demuxer y4m --crf 2.0 --vbv-maxrate 9500 --vbv-bufsize 1835 --keyint 12 --sar 16:9 --bframes 1 --dc 10 --threads 3 --no-progress --mpeg2 -o output.mkv -`

The output format is determined by the extension, although you can specify --muxer mkv. Haali Matroska Muxer is used for mkv (as in x264). Regardless of whether m2v or mpg is specified, it is always output in Elementary stream (but MediaInfo knows the duration). --sar must be specified, even though the yuv4mpegpipe format contains this information. There is a bug. --dar values (the ones people are used to) are understood as --sar.

--cfr sets the quality. 1.0 better quality, higher bitrate, 2.0 worse quality, lower bitrate.  
Instead of uncompressed .y4m the input can be avisynth .avs
