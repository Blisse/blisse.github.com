---
title: word scores
date: 2012-10-05
tags:
  -
    programming
pure_markdown: false
---

<div class="container">
  <div class="sixteen columns">
    <p>
     <img src="http://i.imgur.com/OBg92.jpg" alt="1..26 for a..z" class="scale-with-grid" />
    </p>

    <p>
      From the inspiration above, I decided to check out what words actually fit this definition. Sorry for the Comic Sans in the image, though.
    </p>

    <p>
      First, I'll define
    </p>

    <p>
    {% highlight python %}
      def chars = map ( [char for char in word], range(1,26+1))
      def word_score = sum ( char for char in chars )
    {% endhighlight %}
    </p>

    <p>
      Here's what that looks like in code.
    </p>

    <p>
    {% highlight python %}

    import os, inspect, string
    write_file = "output.txt"
    current_file = "sumofletters.py"
    exceptions = [write_file, current_file]

    output = open(write_file,'w').close()
    output = open(write_file,'a')

    def word_score_list(word):
      return [ (string.ascii_lowercase.find(character)+1) for character in list(word) ]

    def word_score(word): # user-enforce lower case word parameter
      return sum(word_score_list(word))

    def select_word(word, lower_range, upper_range):
      if len(word) > 2:
        if list(word)[-2] == "'" and list(word)[-1] == "s": return False
      if word_score(word) >= lower_range and word_score(word) < upper_range: return True
      return False

    def walk_words(dictionary_path, lower_range, upper_range):
      for word in open(dictionary_path).readlines():
        word = word.strip().lower()
        if select_word(word, lower_range, upper_range) == True:
          output.write( str( ( word, word_score_list(word) ) ).strip("()") + "\n" )

    def walk_dictionaries(current_path, lower_range, upper_range):
      for root, directories, files in os.walk(current_path):
        for dictionary in files:
          if dictionary not in exceptions:
            dictionary_path = os.path.abspath(os.path.join(root,dictionary))
            print "Checking", dictionary_path
            walk_words(dictionary_path, lower_range, upper_range)
      print "Done!"

    def main():
      walk_dictionaries(".", 100, 101)
      output.close()

    if __name__ == "__main__":
      main()

    {% endhighlight %}
    </p>

    <p>
      Not as pretty as it could be, but it works fairly well. <a href="http://pastebin.com/aySiHjUW">Here's the result from my pastebin.</a>
    </p>

    <p>
      Ignoring non-ASCII characters, I get 5340 matches for words that total to 100.
      'Inefficient' appears on there, so I have proven that first image is false with this contradiction.
    </p>

    <p>
      Other interesting words that appear for word_score == 100 are:
        <ul class="square">
          <li>excellent</li>
          <li>snobbery</li>
          <li>socialism</li>
          <li>reengineer</li>
          <li>practicing</li>
          <li>defeminized</li>
        </ul>
    </p>
  </div>
</div>
