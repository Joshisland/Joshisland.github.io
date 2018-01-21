---
layout: post
title: Some experience of using perf.
---
 
I'd like to share some old experience of using perf.

# C exp() function
We have a routine that uses exp() function internally of which arguments are all double. Someday we found that exp() takes more than 30% of the whole running time. At that point, we didn't need precision of 10^-6. So we decided using an appriximate function and it saved a lot of time.

# tcmalloc
We experienced server performance degradations after some hours of the server launch. We ran perf top and found that some tcmalloc functions were using more than 20% of running time. It is weird. Finally we could solve this by upgrading tcmalloc into recent version.


I and my team mates are trying to start using perf and other performance measure tool more seriously. Without knowing our current status, it is hard to make improvement.
