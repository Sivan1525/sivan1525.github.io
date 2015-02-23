---
title: Inject in Ruby
author: sivan1525
layout: post
permalink: /2014/07/inject-ruby/
dsq_thread_id:
  - 2875706642
categories:
  - Ruby
tags:
  - inject
  - Ruby
---
Inject according to the Ruby apidock :

> Inject combines all elements of *enum* by applying a binary operation, specified by a block or a symbol that names a method or operator.

Inject is something what I got hold of now and as I begin to use it I can realize how powerful it is. Using it makes the code more <span data-dobid="hdw">concise</span>.

It is same as ***reduce ***as documented [here][1] .

**Example of reduce and inject:**

<pre class="lang:ruby decode:true "># Sum some numbers
(5..10).reduce(:+)                            #=&gt; 45

# Same using a block and inject
(5..10).inject {|sum, n| sum + n }            #=&gt; 45</pre>

**Example1: Get the sum of a range**

If I have a range: 1..10

<pre class="theme:github font:ubuntu-mono lang:ruby decode:true">(1..10).inject(:+) #=&gt; 55</pre>

** Example2: Get the sum of an array**

<pre class="theme:github font:ubuntu-mono lang:default decode:true ">[1, 2, 3, 4, 5, 6, 7, 8, 9, 10].inject {|res, i| res + i } #=&gt; 5</pre>

** Example3:** **Getting the count of similar strings in a sentence**

<pre class="lang:ruby decode:true ">"The only thing necessary for the triumph of evil is for good men to do nothing.".
split(" ").inject(Hash.new(0)) { |total, e| total[e] += 1 ;total}
#=&gt; {"The"=&gt;1, "only"=&gt;1, "thing"=&gt;1, "necessary"=&gt;1, "for"=&gt;2, "the"=&gt;1, "triumph"=&gt;1, "of"=&gt;1,
"evil"=&gt;1, "is"=&gt;1, "good"=&gt;1, "men"=&gt;1, "to"=&gt;1, "do"=&gt;1, "nothing."=&gt;1}</pre>

&nbsp; 

<div class="pvc_clear">
</div>

<p id="pvc_stats_35" class="pvc_stats " element-id="35">
  <img src="https://railsnuggets.com/wp-content/plugins/page-views-count/ajax-loader.gif" border=0 />
</p>

<div class="pvc_clear">
</div>

 [1]: http://ruby-doc.org/core-1.9.3/Enumerable.html#method-i-reduce "ruby-doc"