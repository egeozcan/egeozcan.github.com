---
layout: post
category : code
tags : [javascript, code, project euler]
---
{% include JB/setup %}

Yet another Project Euler problem, solved with rather brute force. I simply
became too business process oriented to develop clever solutions to mathematical
problems, maybe? =)

## The Problem

Finding the largest palindrome made from the product of two 3-digit numbers.

## The Solution

    var x = 9, y = 9, z = 9; i = 999, found = false, latestPalindrome = 0;
    while(x > 0) {
        if(found) break;
    	y = 9;
    	while(y >= 0) {
    		if(found) break;
    		z = 9;
    		while(z >= 0) {
    			if(found) break;
    			latestPalindrome = parseInt([x,y,z,z,y,x].join(""));
    			for(var i = 999; i >= 100; i--) {
    				if(found) break;
    				if(latestPalindrome % i === 0) {
    					(function(divisionRes) {
    						if (divisionRes.toString().length === 3) {
    							console.log(latestPalindrome, divisionRes, i);
    							found = true;
    						}
    					})(latestPalindrome/i);
    				}
    			}
    			z--;
    		}
    		y--;
    	}
    	x--;
    }
    
Sorry for the lack of elegance. The most interesting thing to learn while coding
this was finding out that <code>parseInt([x,y,z,z,y,x].join(""))</code> was much
faster than <code>(x*100001) + (y*10010) + (z*1100)</code> in JavaScript. Hmm.