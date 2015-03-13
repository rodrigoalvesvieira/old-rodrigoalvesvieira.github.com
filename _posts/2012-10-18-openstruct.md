---
layout: post
title:  "Using OpenStruct for rapid object prototyping in Ruby"
date:   2012-10-18 01:10:38
categories: ruby
---

<span class="drops">W</span>hat if we can quickly build custom data structures and prototype them with no effort? Ruby's `OpenStruct` class is here to help.

{% highlight ruby %}

require "ostruct"

car = OpenStruct.new(brand: "Ford", model: "Phusion", year: 2013, owner_id: 1)

{% endhighlight %}

The [Ruby Quicktips] blog has another good example on how we can use it for app configuration variables.

Jake Scruggs [has also] made a point about using `OpenStruct` for mocking.

I believe this class is more for rapid prototyping purposes. `OpenStruct` is [demonstrably slower] than `Struct` and probably not very reliable to go for production code.

More bad news about it is that it is not as extensible as `Struct`. There is no way for adding methods to it as it relies solely of the `OpenStruct` class itself.

`OpenStruct` is one of Ruby's proof of its own simplicity and dynamism. Hashes that behave like classes? That's definitely cool. It's Ruby's metaprogramming magic all the way until you reach turtles.

Have an opinion about this article? [Discuss on Hacker News].

[has also]: http://jakescruggs.blogspot.com.br/2007/03/using-openstruct-to-enhance-your-mocks.html
[Ruby Quicktips]: http://rubyquicktips.com/post/1718141794/use-openstruct-for-application-configuration-variables
[demonstrably slower]: http://stackoverflow.com/questions/1177594/ruby-struct-vs-openstruct
[Discuss on Hacker News]: https://news.ycombinator.com/item?id=5366968
