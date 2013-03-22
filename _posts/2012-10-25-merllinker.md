---
layout: post
title: CS241 MERL file linker
date: 2012-10-25
tags: [school]
comments: false

pure_markdown: false
archived: true
---

<p>
	For an assignment in my CS241 class, we had to link two <a href="https://www.student.cs.uwaterloo.ca/~cs241/merl/merl.html">MERL files</a> by hand. I didn't want to do this, but I didn't understand the concept of linking MERL files well enough to program a linker to do it for me. I finished the assignment by hand, and after doing that, I could finally complete this linker I was working on. It was an interesting lesson to learn.
</p>

<p>
	I really enjoyed writing the linker, because it was fun to implement an algorithm to parse the input the output with classes, even though my solution is very primitive.
</p>

<p>
	I found out a slightly annoying limitation of Python that I must look for a solution around in the future. Apparently I can't directly read the MERL file directly, so my program's input has to be an xdd file, after running the UNIX xxd utility. Annoying, but I will live with it in the meantime.
</p>

<p>
{% highlight console %}
xxd -c 4 file1.merl > file1.xxd
xxd -c 4 file2.merl > file2.xxd
python linker.py file1.xxd file2.xxd output.txt
{% endhighlight %}
</p>

<p>
	I put the code up <a href="https://github.com/Blisse/MERL-Linker">here</a>.
</p>
