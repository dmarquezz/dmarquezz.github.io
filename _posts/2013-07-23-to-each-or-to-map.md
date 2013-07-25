---
layout: post
title: "Map and Select for Beginners"
tagline: ""
description: ""
category: ruby
tags: [map, collect, select, find_all, arrays, hashes]
---
{% include JB/setup %}

If you're like me, you were introduced to programming through a more traditional programming language. In my case, that language was [Java][java]. In java, your options for iteration are very limited compared to a language like [Ruby][ruby]. The more common methods of iteration in Java are the _for_ and _for-each_ loops. Because these iteration methods are used so frequently in Java, Ruby beginners coming from Java tend to look for a solution that works similary in order to try to solve problems requiring some sort of iteration. A basic example of this mistake is filling an array:

{% highlight ruby %}
#!/usr/bin/env ruby

evens = [2, 4, 6, 8]
odds = []
evens.each { |num| odds << num += 1 }
# now odds = [3, 5, 7, 9]
{% endhighlight %}

similarly:

{% highlight ruby %}
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9]
odds = []
nums.each { |num| odds << num if num%2 != 0 }
# now odds = [1, 3, 5, 7, 9]
{% endhighlight %}

This is a common mistake I made when learning Ruby. "But this solution works!" some, like I once did, might argue. Your argument is correct, however; Ruby offers us a more concise, better looking solution, which is a [functional programming][functionalprogramming] style of solving this sort of problem.

The solutions that I am talking about are [_map_][map] and [_select_][select]. _map_ and _select_ are both methods in Ruby's Enumerable module. Since Enumerable is mixed into several classes, we can call these methods on arrays and hashes, amongst other things.

_map_ iterates over an array and runs a block of code on each element of that array. When it is done iterating, it returns a _new_ array with the newly computed values. Therefore, we can solve the problem in the first example in the following way using _map_: 

{% highlight ruby %}
#!/usr/bin/env ruby

evens = [2, 4, 6, 8]
odds = evens.map { |num| num += 1 } 
#=> [3, 5, 7, 9]
{% endhighlight %} 

_select_ also iterates over each element in an array. The difference however, is that _select_ returns a new array composed of the elements "for which the given block is true." Therefore, we can solve the problem in the second example in the following way using _select_:

{% highlight ruby %}
nums = (1..9)
odds = nums.select { |num| num%2 != 0 } 
#=> [1, 3, 5, 7, 9]
{% endhighlight %}

Something to note is that these methods will always return an array. This means that if you use these methods on a hash in the way I do so above, you will still get a new array - not a new hash. If you're looking for a solution to mapping hashes, [check out the answer to this question on SO.][so]
 

[java]: http://docs.oracle.com/javase/tutorial/java/
[ruby]: http://www.ruby-lang.org/en/
[functionalprogramming]: http://en.wikipedia.org/wiki/Functional_programming
[map]: http://ruby-doc.org/core-2.0/Enumerable.html#method-i-map
[select]: http://ruby-doc.org/core-2.0/Enumerable.html#method-i-select
[so]: http://stackoverflow.com/questions/4137824/how-to-elegantly-rename-all-keys-in-a-hash-in-ruby
