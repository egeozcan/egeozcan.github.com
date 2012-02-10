---
layout: post
category : code
tags : [javascript, code, project euler]
---
{% include JB/setup %}

I wanted to share my boring solution to [Problem 3](http://projecteuler.net/problem=3) on [Project Euler](http://projecteuler.net/).

## The Problem

What is the largest prime factor of the number 600851475143?

## Solution

    var originalTarget = 600851475143;
	var target = originalTarget;
	var i = 2;
	while(i<target) {
		while(target%i === 0) {
			(function(newtarget) {
				console.log(target + " can be divided by " + i + " which gives us " + newtarget);
				target = newtarget;
			})(target / i)
		}
		i++;
	}
	console.log("it seems like " + target + " is the biggest prime factor for " + originalTarget);
	
That should do it. There could be some room to improve, however.
