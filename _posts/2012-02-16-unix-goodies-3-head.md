---
layout: post
title:  "Unix Goodies: head"
date:   2012-02-16 01:10:38
categories: unix
---

<span class="drops">W</span>e often need to quickly read the contents of files in the console. Sometimes the file is just too big and we want to read only the first lines so `cal` ins't appropriate. When this is the case, **head** to the rescue!

The _head_ tool does just this, tell us only the first lines of a given file.

<pre class="terminal">
  $ head file.html
</pre>

Did you think about printing the "heads" of multiple files?

<pre class="terminal">
  $ cat file.html file.rb
</pre>

Now, of course you may want to print only the first **number** lines of a file, assuming that `number = 1`:

<pre class="terminal">
  $ cat -n number script.rb
</pre>

That's it, hope _head_ helps you! (It'll most likely do :) )
