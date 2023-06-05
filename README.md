# Scripts for organizing music library

## MusicBrainz Picard

**Make sure that the "Join multiple ID3v2.3 tags with:" option is set to ";" rather than "/".**

### Additional files to move
```
*.jpg *.png *.log *.cue *log.txt *.pdf *.lrc *.accurip auCDtect.txt *.m3u *.m3u8 *.nfo Album Art\*
```

Rest of the scripts are in separate files.

## Exact Audio Copy 

### Encode settings for FFmpeg
```
-i %source% -metadata "ARTIST=%artist%" -metadata "TITLE=%title%" -metadata "ALBUM=%albumtitle%" -metadata "DATE=%year%" -metadata "TRACKNUMBER=%tracknr%" -metadata "GENRE=%genre%" -metadata "PERFORMER=%albuminterpret%" -metadata "COMPOSER=%composer%" -metadata "ALBUMARTIST=%albumartist%" -metadata "DISCNUMBER=%cdnumber%" -metadata "TOTALDISCS=%totalcds%" -metadata "TOTALTRACKS=%numtracks%" -metadata "COMMENT=%comment%" -codec:a flac -compression_level 12 %dest%
```

### Encode settings for Flac
```
-8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T "COMMENT=%comment%" %source% -o %dest%
```

I strongly recommend setup other settings according to these guides:
- http://doujinstyle.com/eac/setup.html
- http://doujinstyle.com/eac/ripping.html

## Foobar2000

### Media library album list
```
[%album artist% - ]%directoryname%$ifgreater(%totaldiscs%,1,|Disc %discnumber%,)|$ifgreater(%totaldiscs%,1,%discnumber%.,)%tracknumber% [%track artist% - ]%title%
```

### Audio scrobbler `artist` field remap
```
[$if2(%album artist%,$meta(artist,0))]
```
