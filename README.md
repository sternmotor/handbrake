# handbrake
DVD ripper script running dockerized handbrake

The `rip` script thankfully pulls [jlesage/handbrake][] and pre-configures for ripping video in a decent quality plus english and german audio tracks and subtitles. This is meant to help through the jungle of handbrake options.

Constant quality is prefered over constant bitrate by default.

Container format is mkv since there have been issues embedding subtitles in mp4. These two are the most common as of the time of writing this script.

The following quality settings may be applied (see `-q|--quality` option below):

* `-q 18`: DVD Rip (SD Quality) DVD_720_480, X264_LEVEL=3.1 14 Mbit/sec
* `-q 20`: HD Blue Ray FHD_1920_1080, x264_level=4.1 50Mbit/s
* `-q 22`: 4K Blue Ray UHD_3840_2160, x264_level=5.1 240 Mbit/s

See [Wikipedia H.264][] for more details.


Main options and commands
-------------------------

Run the script to scan main title for chapters, audio and subtitle info. Thsi information may be useful for the actual ripping in the next step

	./rip --scan
	./rip -s

After this, start ripping - eventually apply the following options:

* `-u|--sub`: select subtitles like `1,2,3` 
* `-a|--audio`: select audio track like `1,2,3` 
* `-q|--quality`: specify quality option `20` or `22` for improving quality - default is 18 (see "quality settings" comment above)
* `-t|--targetdir`: directory where movie is to be stored in (a subdirectory will be created named like the movie)
* `-n|--name`: specify title like "Der Film Name" 


[jlesage/handbrake]: https://github.com/jlesage/docker-handbrake
[Wikipedia H.264]: https://de.wikipedia.org/wiki/H.264#Level
