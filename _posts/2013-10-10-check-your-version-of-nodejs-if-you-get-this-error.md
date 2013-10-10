---
layout: post
title: "Check Your Version of NodeJS If You Get This Error"
categories:
- articles
tags:
- sysadmin
- ubuntu
- linuxmint
- nodejs
- grunt
---


I am sharing a head-desk moment that I had yesterday, in hopes that it could help somebody. The CSS on this new blog of mine wasn't updating after changing the [Less][4] files. This blog runs on [Jekyll][1] with the [Minimal Mistakes][2] theme, and I hadn't yet tried to tweak the CSS (as evidenced by the many rough edges around this place). Turns out, I needed to run [Grunt][3] to update the CSS, so I installed Grunt, installed the rest of the project's package dependencies from 'packages.json', and hoped for the best: that grunt would start recompiling my CSS.

    npm install -g grunt
    npm install

    $ grunt
    node.js:201
            throw e; // process.nextTick error, or 'error' event on first tick
                  ^
    TypeError: Object #<Object> has no method 'existsSync'

Oops. Long story short, if you get this error out of a Node app, check your versions on everything. I checked npm (1.3.8). Good. I checked grunt (0.4). Good. Then I checked node.js. 0.6.12. *Ancient.* That's what I get for relying on Linux Mint 13's outdated packages for Node. Installing the latest binaries (0.10.20) fixed it right up.

> And that's why you should always check your package versions!

*This was particularly a head-desk moment because I had discovered earlier in the day that I was still running an older and buggy version of [ack](http://betterthangrep.com).*

[1]: http://jekyllrb.com/
[2]: http://mademistakes.com/articles/minimal-mistakes-jekyll-theme.html 
[3]: http://gruntjs.com/
[4]: http://lesscss.org/
