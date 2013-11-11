---
layout: post
category : code
tags : [javascript]
---
{% include JB/setup %}

Well, [here](https://news.ycombinator.com/item?id=6527104) is an interesting poll.
In my opinion, the userbase of HN tends to be more open and experimental than the average programmer crowd and
that makes these results even more interesting to me:

     0. Python 2093
     1. C 1629
     2. Go 765
     3. SQL 704
     4. Haskell 691
     5. JavaScript 683
     6. C# 665
     7. Lisp 635
     8. Clojure 571
     9. Scheme 523
    10. Ruby 489
    11. Lua 486
    12. Assembly 371
    13. Erlang 371
    14. Rust 318
    15. Scala 217
    16. OCaml 203
    17. F# 173
    18. Smalltalk 144
    19. Shell 131
    20. Forth 128
    21. D 88
    22. Other 65
    23. R 50
    24. Ada 14
    25. Pascal 11
    26. Rexx -53
    27. Delphi -94
    28. Tcl -98
    29. Fortran -132
    30. Groovy -155
    31. CoffeeScript -159
    32. Objective-C -215
    33. Perl -256
    34. C++ -345
    35. Cobol -443
    36. ColdFusion -560
    37. Actionscript -661
    38. Java -931
    39. Visual Basic -957
    40. PHP -1360

ps. I used the following quick-and-dirty script to parse the results. You can get the current results by running this:

    var scores = {}, name, sign;
    [].slice.call($0.querySelectorAll("tr:not([style])"), 0).forEach(function(row, i) {
        if(i%2 === 0) {
            var nameAndSign = row.innerText.trim().split(" - ");
            name = nameAndSign[0];
            sign = nameAndSign[1] === "Like" ? 1 : -1;
        }
        else {
            scores[name] = scores[name] || 0;
            scores[name] += sign * parseInt(row.innerText.trim().split(" ")[0]);
        }
    });
    var scoresArray = []; Object.keys(scores).forEach(function(key) { var entry = {}; entry[key] = scores[key]; scoresArray.push(entry); });
    scoresArray.sort(function(b,a) { return a[Object.keys(a)[0]] - b[Object.keys(b)[0]]; });
    scoresArray.forEach(function(a) { var name = Object.keys(a)[0]; console.log(name, a[name]) });
