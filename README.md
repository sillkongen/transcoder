# transcoder
FFmpeg transcoding and watermarking script.

The general idea was to be able to watermark advertising clips while working on the SkyGo adsmart project. James Hart figured out what/how the transcoding would need to be.

I am the lazy one so I came up with a one liner to generate a list of items to transcode from a folder.

ls -l | awk '{  print "ffmpeg -i "$9 " -i Brave.png  -filter_complex '""overlay=10:10""' -c:a copy  -c:v libx264 -profile:v main -b:v 8156k -c:a copy " $9}' | awk '{print substr($0, 0, length($0)-4) "-watermarked.mp4"}'
