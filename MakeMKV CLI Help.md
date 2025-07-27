# Overview
> This content was taken from the following site:
> [https://www.makemkv.com/developers/usage.txt]
# Helpful Content
| Command | Content |
| ------- | ------- |
|--messages=file|Output all messages to file. Following special file names are recognized:<ul><li>-stdout - stdout</li><li>-stderr - stderr</li><li>-null - disable output</li></ul>Default is stdout|
|--progress=file|Output all progress messages to file. The same special file names as in --messages are recognized with additional value "-same" to output to the same file as messages. Naturally --progress should follow --messages in this case. Default is no output.|
|--debug[=file]|Enables debug messages and optionally changes the location of debug file. Default: program preferences.|
|--directio=true/false| Enables or disables direct disc access. Default: program preferences.|
|--bindport=port| Specify web server port to bind. Default: 51000.|
|--minlength=seconds| Specify minimum title length. Default: program preferences.|
|-r , --robot| Enables automation mode. Program will output more information in a format that is easier to parse. All output is line-based and output is flushed on line end. All strings are quoted, all control characters and quotes are backlash-escaped. If you automate this program it is highly recommended to use this option. Some options make reference to apdefs.h file that can be found in MakeMKV open-source package, included with version for Linux. These values will not change in future versions.|