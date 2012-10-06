---
layout: post
title: word scores
date: 2012-10-05
tags: [programming]
---

 <img src="http://i.imgur.com/OBg92.jpg" alt="1..26 for a..z" class="scale-with-grid" /> 

<p>
  From the inspiration above, I decided to check out what words actually fit this definition. Sorry for the Comic Sans in the image, though.
</p>

<p>
  First, I'll define 
</p>

{% highlight python %}
  def chars = map ( [char for char in word], range(1,26+1))
  def word_score = sum ( char for char in chars )
{% endhighlight %}

<p>
  Here's what that looks like in code.
</p>

{% highlight python %} 

import os, inspect, string
write_file = "output.txt"
exceptions = [write_file, inspect.stack()[0][1]]

def word_to_number(word,lower_range,upper_range): # enforce lower case input parameter
  s = 0
  for character in list(word):
    if string.ascii_lowercase.find(character) != -1: s += string.ascii_lowercase.find(character)+1
    else: pass
  if s>=lower_range and s<upper_range:
    return s
  return -1

def read_dictionary(dictionary_path):
  return [ word for word in open(dictionary_path).readlines() if word_to_number(word,100,101) != -1]

def dict_walk(current_path):
  s = []
  for root, directories, files in os.walk(current_path):
    for dictionary in files:
      if dictionary not in exceptions:
        print "Checking", os.path.join(root,dictionary)
        s += read_dictionary(os.path.abspath(os.path.join(root, dictionary)))
  print "Done!"
  return s

def main():
  output = open("output.txt",'w').close()
  output = open("output.txt",'w')
  output.write("".join(dict_walk(".")))

if __name__ == "__main__":
  main()
{% endhighlight %}

<p>
  Not as pretty as it could be, but it works fairly well.
</p>

<p>
  Ignoring non-ASCII characters, I get 6771 matches for words that total to 100. 
  'Inefficient' appears on there, so I habve proven that first image is false via contradiction.
</p>

<p>
  Other interesting words that appear for word_score == 100 are:
    <ul class="square">
      <li>maximize
      <li>analysis
      <li>attitude //good thing it does
      <li>excellent
      <li>culture
      <li>hospital
      <li>printer
      <li>personal
      <li>telephone
      <li>lightning
      <li>unavailable
      <li>chimpanzee
      <li>theists
      <li>egotistical
      <li>hiroshima
    </ul>
    
</p>