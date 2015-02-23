---
title: Multiplication matix  in ruby
author: sivan1525
layout: post
permalink: "/2015/02/multiplication-matix-in-ruby/"
dsq_thread_id: 
  - 3516091631
categories: 
  - Ruby
tags: 
  - Ruby programs
published: true
---

## Multiplication matix in ruby :

Description:

Print out the table in a matrix like fashion,  
each number formatted to a width of 4 (The  
numbers are right-aligned and strip out  
leading/trailing spaces on each line).  
The first 3 line will look like:

> 1   2   3   4   5   6   7   8   9  10  11  12  
2   4   6   8  10  12  14  16  18  20  22  24  
3   6   9  12  15  18  21  24  27  30  33  36

&nbsp;

Solution:

> <pre class="tab-size:2 lang:default decode:true"for i in 1..12
  for j in 1..12
    print "#{i*j}".rjust(4) # http://stackoverflow.com/a/15021531/1542202
    puts "" if j == 12
  end
end</pre

An interesting method I came across was <span style="text-decoration: underline;">rjust</span> , which helped in right aligning the string . Similar to rjust there is <span style="text-decoration: underline;">ljust</span> which is used for left aligning of string.

Further details can be found here:

http://apidock.com/ruby/String/rjust and http://apidock.com/ruby/String/ljust .