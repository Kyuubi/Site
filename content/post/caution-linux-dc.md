+++
date = "2017-07-01T12:00:00"
draft = false
tags = ["linux DC++", "missing downloads"]
title = "Linux DC++ problem"
math = true
summary = """
A cautionary note to linux DC++ users
"""

#[header]
#image = "/home/pain/Downloads/chebyshev.png"
#caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"

+++

Linux DC++ is a quite popular File sharing application used on the Linux OS. It looks something like this …

![LinuxDC++](../../img/linuxdc.png)

One of the major benefits which I saw with Linux DC++ compared to its alternatives like Eiskalt DC++ is that Linux DC++ consumes a relatively smaller amount of RAM and doesn't lag the system which I found to be a big drawback for Eiskalt DC++


Anyway, there was one erratic behavior which I was quite irritated about in Linux DC++. At some random time on some random you are peacefully downloading stuff from DC and then suddenly the entire downloads directory is missing.


You already have space constraints in your system and then the downloads folder with some very *ahem ahem* important files just goes away and worse … the space is not even empty.


So started looking up the bug, and viola found it.


You can find all your stuff in folders within ~/.dc++/FileLists/. There will be a lot of folders with very weird names and all of your deleted stuff will be inside there. Just have to bring them out using the mv command.
## License

Copyright 2017 [Parth Thaker](https://parththaker.github.io/).

Released under the [MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) license.
