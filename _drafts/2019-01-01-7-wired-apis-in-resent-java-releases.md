---
layout: post
title:  "7 Controversial APIs You Can Find in Resent Java Releases"
date:   2019-01-01 10:00:00 +0200
comments: true
---
Java has recently received a new release cycle in which updates
are smaller but more frequent. Since then we've got many useful
features which are appreciated among the community. But at the same
time there has been some questionable features which are rather
misleading. I will list some of such features introduced in Java 9 - 11.
If you know more - please comment them down below.

{% 
  include picture.html 
  href="2019-01-01-roknrolla.jpg" 
  copyright="RocknRolla by Guy Ritchie"
  alt="Scene from RocknRolla"
%}

**You can now remove all leading and trailing space from a sting.** You'll 
probably say that you can remove them already using `String.trim()` and you
will be right. But in Java 11 a new method has been introduced: `String.strip()`.
Here is what the documentation of `strip()` says:
> Returns a string whose value is this string, with all leading and trailing 
white space removed

And here is the documentation of `trim()`:
> Returns a string whose value is this string, with all leading and trailing 
space removed

Look similar, don't they? There of course was a reason why they did this. The 
reason is in what they define as a space. In `trim()`, space is defined
as any character whose codepoint is less than or equal to 'U+0020' (the space character). 
Which means that `trim()` removes some limited set of space characters. At the same time
`strip()` removes all that are not handled by `trim()`. Why didn't they just fix `trim()`?
Because there is a backward compatibility in Java. If they had fixed it a lot of old code
would have been broken. But what this means for us - developers is that we'll have to deal
with it. We'll have to remember not o use `trim()`, etc.

**You can now launch single-file source-code programs without compilation.** Which means
that if you have a hello-world-like program you can skip the compilation phase and run the
file directly. 
Before:
```
javac HelloWorld.java && java HelloWorld
``` 
After
```
java HelloWorld.java
```
It is an improvement. But who they target it to? Not that I don't launch single-file
programs - it happened a few times. I did it when I started learning Java, then it happened
when I showed how to compile and run a program to my friend and the third time was while writing this
article. That's it. Has it improved my life? No.

I guess it is a confusing thing for Java learners. You run you first program using this simple 
way and you're happy that it is so easy and then you add one more class and it stops working.

**Factory methods in `Map` interface.** This is no doubt a useful feature. I use it a lot and it does 
simplify my code. The only thing I don't 