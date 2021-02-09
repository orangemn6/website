---
title: "Making a Simple Url Shortner With Netlify"
author: Jacob Goldstein
date: 2021-02-09T08:46:51-05:00
draft: false
type: post
categories:
 - webdev
 - web-dev
tags:
 - webdev
 - web-dev
---

## Starting

So, I made a new URL shortener, [jgold.tk](https://jgold.tk), and if you click that link it will redirect right back to this site. Now if you go to [jgold.tk/mc](https://jgold.tk/mc), it redirects to Jacob MC. I am going to show you how to do this

## Setting up netlify

So you have 2 options here:

1. Set up your own repo
2. Clone mine

I am gonna show you how to do number 1

So first, make a github repo. I called mine jgold.tk because that is the shortener. Clone that repo locally, you know the drill. `cd` into it. Now make a package.json with this inside:

```json
{
  "baseUrl": "https://jgold.tk",
  "private": true,
  "scripts": {
    "shorten": "netlify-shortener"
  },
  "author": "orangemn6",
  "devDependencies": {
    "netlify-shortener": "^1.0.1"
  }
}
```

So what this does is it tells netlify that it needs the netlify-shortener package. Now we start the shortener part.

## Redirects

So, make a file called `_redirects`, and inside of it put a structure like this:

```
/blog        https://jacobgoldstein.tk/posts
/tw          https://twitter.com/orangemn6
/gh          https://github.com/orangemn6
/mc          https://play.jacobgoldstein.tk

#fallback
/*           https://jacobgoldstein.tk
```

What this does is it tells netlify, here are my redirects. Now, git add, git commit, and git push.

## Adding to netlify

Now, make a new netlify site and connect the github repo to it (Note: this will also work with gitlab). Now, add your domain into netlify, setup Netlify DNS, and wait a minute. Now go to yourdoma.in/whatever and see your url shortener work!

## Conclusion

Well, now you know how to make a URL shortener with netlify. If you have any questions, contact me or comment below!
