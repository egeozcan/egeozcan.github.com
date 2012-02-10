---
layout: post
category : code
tags : [javascript, code, project euler]
---
{% include JB/setup %}

## The Problem

What is the smallest positive number that is evenly divisible by all of the
numbers from 1 to 20?

## The Solution

	var from = 1, target = 20, primes = {}, result = 1;
	
	for(var divider = from; divider <= target; divider++) {
		(function(newTarget) {
			var i = 2, dividersPrimes = {};
			while(i <= newTarget) {
				while(newTarget % i === 0) {
					newTarget = newTarget / i;
					if(!dividersPrimes[i]) {
						dividersPrimes[i] = 1;
					}
					else {
						dividersPrimes[i]++;
					}
				}
				i++;
			}
			for(var prime in dividersPrimes) {
				if(dividersPrimes.hasOwnProperty(prime) 
					&& (!primes[prime] 
						|| primes[prime] < dividersPrimes[prime])) {
					primes[prime] = dividersPrimes[prime];
				}
			}
		})(divider)
	}
	for(var prime in primes) {
		if(primes.hasOwnProperty(prime)) {
			result = result * Math.pow(prime,primes[prime])
		}
	}
	console.log(result);
	
I know this can be calculated very easily with pen and paper but
overcomplicating stuff is just fun, I guess =)