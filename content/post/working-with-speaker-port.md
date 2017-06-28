+++
date = "2017-07-01T12:00:00"
draft = false
tags = ["audio sink", "noise generation"]
title = "Experimentation with audio sink"
math = true
summary = """
A experiment journal entry for audio sink
"""

#[header]
#image = "/home/pain/Downloads/chebyshev.png"
#caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"

+++

First I tried experimenting , first good/cool thing I found was this command : 
```
cat /dev/urandom | padsp tee /dev/audio > /dev/null
```

OR 
```
cat /dev/urandom | padsp tee /dev/dsp > /dev/null
```

Both produces white noise in speakers. 


On good/sad thing is it sends to the audio sink you have... If the comp is on speaker mode... the noise will be in your speakers

If there are headphones, it will be your headphones..


But on trying to do something like this:

```
cat <somefile>.mp3 | padsp tee /dev/audio > /dev/null
```

 Unsurprisingly it didn't work. Reason : My speculation, .mp3 is a coding format and it might not have suited the format in which /dev/audio wanted it... 


On to next cool thing (found a lot of them while tweaking things) is the program called mpg123. It is used as:

```
mpg123 <somefile>.mp3 | /dev/pcsp
```

`/dev/pcsp` basically is your speaker. `mpg123` decodes .mp3 file into raw streaming data which is piped ('|') to speakers


A good thing about speakers is that it can overlap all noises no locking system as to who can write and stuff. Nice one...


Ok.. So we got a way in which we can run raw data streams into speakers. Now how about capturing what is being run to the speakers. In other words snooping on the /dev/pcsp (I am not sure /dev/pcsp is the right place to snoop.)

```
arecord -f cd -t raw
```

The above command starts recording whatever is heard on the speakers. Now to pipe it to a music file we use the 'oggenc' package. So finally its

```
arecord -f cd -t raw | oggenc - -r -o file.ogg
```

This will create a music file in the current directory which is capturing all of the sound played in your speakers.


So where are we right now. We have a way to play to a speaker, we have a way to record from a speaker. Now the remaining is to make a connection.


Supporting articles :

* [https://debian-administration.org/article/145/use_and_abuse_of_pipes_with_audio_data](https://debian-administration.org/article/145/use_and_abuse_of_pipes_with_audio_data) 

> This article deals with piping raw data to files of 0 byte size (FIFO files) and then playing it. 

* [https://debian-administration.org/article/58/Netcat_The_TCP/IP_Swiss_army_knife](https://debian-administration.org/article/58/Netcat_The_TCP/IP_Swiss_army_knife) 

> This article deals with using `netcat` for listening and sending data on ports.

## License

Copyright 2017 [Parth Thaker](https://parththaker.github.io/).

Released under the [MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) license.
