---
layout: post
title:  "Instances of TrueClass and FalseClass could have to_i"
date:   2012-02-09 01:10:38
categories: ruby
---

<span class="drops">T</span>oday, in a Rails app, I needed to represent a boolean attribute coming from the database as either 1 or 0, then I called the `to_i` method on this attribute and boom! `NoMethodError`. Here's the obvious implementation of these methods:

{% highlight ruby %}

class TrueClass
  def to_i
    return 1
  end
end

class FalseClass
  def to_i
    return 0
  end
end

true.to_i # => 1
false.to_i # => 0

{% endhighlight %}

It first seemed reasonable to me to have `true` and `false` represented also as integers but as my friend [Nathan Proença] pointed out, this could be easily used for bad purposes:

{% highlight ruby %}

true.to_i + true.to_i # => 2

# Worse stuff below:

var = 0

var == 0 # => true

(var == 0).to_i #=> 1

{% endhighlight %}

I think this explains why Ruby doesn't implement this method. If you have any additional info on this topic, please leave it in the comments!

[Nathan Proença]: https://twitter.com/#!/_na2th
