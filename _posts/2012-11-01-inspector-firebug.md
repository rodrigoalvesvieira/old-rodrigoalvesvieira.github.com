---
layout: post
title:  "Web Inspector and Firebug element selection trick"
date:   2012-11-01 01:10:38
categories: ruby
---

<span class="drops">S</span>o you are inspecting elements via the Web Inspector on Chrome/Safari or the Firebug on Firefox and you wanna play with those elements you just selected in the console.

Normally what you'd do is record the element's class name or id and use jQuery (let's assume you're using jQuery for brevity's sake) to select it, like this:

{% highlight javascript %}

$(".github-logo-4x-hover");

{% endhighlight %}

But here's a nice trick to speed this up for you. In both Web Inspector and Firebug you're allowed to refer to a few previously selected elements with the aliases <span class="small_code">$0</span>, <span class="small_code">$1</span>, <span class="small_code">$2</span>, <span class="small_code">$3</span> and <span class="small_code">$4</span>.

See the example:

Here I select the element:

[![Selecting an element on the Web Inspector](/images/inspector-firebug/element_selection.png "Selecting an element on the Web Inspector")](http://www.rodrigoalvesvieira.com/images/inspector-firebug/element_selection.png)

Now it can be accessed via the Console through the <span class="small_code">$0</span> variable:

[![Fetching the last selected element on the Web Inspector](/images/inspector-firebug/element_selection1.png "Fetching the last selected element on the Web Inspector")](http://www.rodrigoalvesvieira.com/images/inspector-firebug/element_selection1.png)

<span class="small_code">$0</span> exactly corresponds the last selected element. <span class="small_code">$1</span>, <span class="small_code">$2</span>, <span class="small_code">$3</span> and <span class="small_code">$4</span> correspond to the other previously selected elements in reverse order.

jQuery, for example, can deal with these variables just well:

{% highlight javascript %}

$($0).click(function () {
    alert("You have clicked it!");
});

{% endhighlight %}

This is a simple trick, but can really help us during our day-to-day software craftsmanship.
