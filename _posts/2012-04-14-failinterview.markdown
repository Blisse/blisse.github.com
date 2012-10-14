---
layout: post
title: first coding interview
date: 2012-04-14
tags: [fails, school]
---

<p>
	I had an interview the other day that really shook me up.

	He asked me a question that really made me wonder how much I really knew about programming. 
	I really thought I knew Python (at least somewhat decently), but I understand now there's a difference between using a language a few times, and actually knowing the language in and out.

	My answer was... "crap." I did not know what to do really, and it cost me the interview. I was ashamed, and now that I try it, I should've known it. 

	The question was (I think): 
</p>


{% highlight console %}

Remove the first letter from each word in the string: 
> "asdf das f po"

{% endhighlight %}

<p>
	EDIT(2012-07-16): This was my March attempt.
</p>


{% highlight python %}

# removes spaces from string

line = original
newline = ""

for i in line:
	if ord(i) != (ord(' ')):
		newline += i
	else:
		pass
		
print newline

# removes first letter of each word from string and fixes spacing

line = original
newword = ""

first = 1

newline = []

for word in line.split():
	for letter in word:
		if first != 1:
			newword += letter
		else:
			first = 0
			
	first = 1
	newline.append(newword)
	newword = ""

output = []

for word in newline:
	if word == '' or word == ' ':
		pass
	else:
		output.append(word)

newline = " ".join(output)
print newline

{% endhighlight %}

<p>
	EDIT(2012-07-16): How did I not realize how bad this was back when I wrote it? 
	Wow. Just wow. I don't know how I made it this far programming if that was the best I could 
	come up with. Honest.
</p>

{% highlight python %}

def removefirstletter( sentence ):
	tokens = sentence.split()
	for word in range(len(tokens)):
		tokens[word] = "".join(list(tokens[word])[1:])
	return " ".join(tokens)

{% endhighlight %}

<p>
	Easily handles any issue with spacing when you remove the word with one letter.

	The output should be 
</p>

{% highlight console %}

> "df as o"

{% endhighlight %}

<p>
	I'd like to think I made progress, but this could be done a lot better still. 
	But if I got this far in 3 months, I'm can't think of the possibilities in a couple years!
</p>