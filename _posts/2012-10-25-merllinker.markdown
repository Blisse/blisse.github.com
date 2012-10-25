---
layout: post
title: cs241 merl file linker
date: 2012-10-25
tags: [school]
---

<p>
	For an assignment in my CS241 class, we had to link two merl files by hand. I didn't want to do this, but I didn't understand the concept of linking MERL files well enough to write a linker for them. I finished the assignment by hand, but after doing that, I could finally complete the linker I wrote for it.
</p>

<p>
	I really enjoyed writing it, because it looked very fun to implement an algorithm with classes like this, even though my solution is very primitive.
</p>

<p>
	I found out a slightly annoying limitation of Python. Apparently I can't directly read the merl file, so my program's input is a .xdd file. The entire program can be run by the following commands.
</p>

<p>
{% highlight console %}
xxd -c 4 file1.merl > file1.xxd
xxd -c 4 file2.merl > file2.xxd
python linker.py file1.xxd file2.xxd output.txt
{% endhighlight %}
</p>

<p>
	You can find the code on my GitHub file, <a href="https://github.com/Blisse/MERL-Linker">here</a>.
</p>