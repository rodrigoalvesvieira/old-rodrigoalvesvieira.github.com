---
layout: post
title:  "Mutate Method Visibility on the Go in Ruby"
date:   2012-01-02 01:10:38
categories: ruby
---

<span class="drops">R</span>uby is extremely flexible - for programmer's joy or madness - it lets you change almost anything at will. Well, method visibility too.

Look at the following code snippet:

{% highlight ruby %}

class Father

  def bank_account
    "called from #{self}"
  end

  protected :bank_account
end

tom = Father.new
tom.bank_account

# => NoMethodError: protected method `bank_account'
# called for #<Father:0x007fed0d05c128>

class ShamelessSon < Father
  public :bank_account
end

dillinger = ShamelessSon.new
dillinger.bank_account

# => Called from #<Son:0x007f8ea40bfee8>

{% endhighlight %}

In the `ShamelessSon` class, we told Ruby to mark the `bank_account` method as public, making it available to this class' instances to use, in this case, `dillinger`.

Needless to say, this technique is dangerous. Use it wisely, only redefining visibility of the methods from the classes that you **know** and **trust**.
