---
layout: post
title: Some experience of using perf.
---
 
I'd like to share some old experience of using perf.

# C exp() function
It was 3~4 years ago. We have a routine that compares two binary strings, query and reference, for deciding they are similar or not. It uses a lot of Hamming distance computation using popcount and we had a belief that popcount is the main bottleneck. Maybe we made such a belief because introducing popcount intrinsic gave huge boost on the running time. Before popcount intrinsic, it was true, and maybe we didn't check the real numbers after then. However, it is revealed that exp() function that is for computing threshold value for the similarity uses more than 30% of time. We all were astonished. From the observation that arguments of exp() function are all doubles and quite small and the fact that we didn't need precision of 10^-6, we decided using an appriximate function and it saved a lot of time.

# tcmalloc
We experienced server performance degradations after some hours of the server launch. We ran perf top and found that some tcmalloc functions were using more than 20% of running time. It is weird. Finally we could solve this by upgrading tcmalloc into recent version. Related tcmalloc issue can be found at https://github.com/gperftools/gperftools/issues/446


I and my team mates are trying to start using perf and other performance measure tool more seriously. Without knowing our current status, it is hard to make improvement.
