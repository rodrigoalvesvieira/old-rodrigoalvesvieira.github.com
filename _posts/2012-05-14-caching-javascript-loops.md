---
layout: post
title:  "Caching JavaScript Loops"
date:   2012-05-15 01:10:38
categories: javascript
---

<span class="drops">L</span>oops - don't matter what code you're writing - are potential expensive tasks. They can also be performing critical blocking operations in your code, slowing it down. When possible (and/or needed), it is useful to cache your loops.

JavaScript lets you cache `for` loops in a simple way.

Let's think of a scenario, in which we have a great many `<li>` tags representing car models in our documents. Each of these elements have a HTML5 `data-name` attribute that contains the model name of the vehicle. In the following code we iterate over all `li`s on the document, fetching their model names and storing it in an array of names, defined blank, before the loop:

{% highlight js %}

var carNames = [],
    carListings = document.getElementsByTagName("li");

for (var i=0; i < carListings.length; i++) {
  var listing = carListings[i];
  carNames.push(listing.getAttribute("data-name"));
}

{% endhighlight %}

The problem with the approach in the algorithm above is that JavaScript will keep querying the `carListings` length while it is greater than `i`. We can prevent that from happening by querying the `carListings` length only once and storing it in a variable so that this one variable would be queried by the running loop:

{% highlight js %}

for (var i=0; size = carListings.length; i < size; i++) {
  var listing = carListings[i];
  carNames.push(listing.getAttribute("data-name"));
}

{% endhighlight %}

Depending on the task you're performing, you may notice significative performance improvements by using this method. Additionally, this method does not leave the code less readable and perhaps should always be used.
