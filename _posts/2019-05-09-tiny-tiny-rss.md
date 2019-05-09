---
layout: post
title:  "Tiny Tiny RSS"
---

As part of my ongoing effort to decentralize my use of the web, I'm now hosting
a web-based RSS feed reader called Tiny Tiny RSS. This post provides setup info
if you have an account on fogcloud.org

## What is RSS? Why?

RSS is a standard for distributing "feeds" of updates to websites. This makes it
easy to follow a bunch of websites that update periodically without having to
visit all of them to check for updates.

Examples of things that are drastically improved by an RSS reader:

 * Blogs
 * Web comics
 * News sites

This is great for you as a user, since it allows you to see *all* the posts on
sites you're interested in without any mediation by a centralized service like
Facebook.

It's also great if you make content yourself, since it gives you a way to push
stuff directly to your audience if they subscribe to your feed.

## Log In

The reader is hosted at <https://feeds.fogcloud.org/>

Log in with your fogcloud username and password.

## Set Up Your Browser

Browsers used to provide native RSS support, but the major ones have removed
this functionality because it "wasn't sufficiently popular" (read: conflicted
with their advertising-based business models).

Luckly, third party addons provide support.

### Browser: Firefox

Install these two addons:

 * <https://addons.mozilla.org/en-US/firefox/addon/awesome-rss/>
 * <https://addons.mozilla.org/en-US/firefox/addon/tiny-tiny-rss-watcher/>

Configure both addons with the URL to the tt-rss instance (
https://feeds.fogcloud.org/ ).

### Browser: Chrome

Install these two addons:

 * <https://chrome.google.com/webstore/detail/rss-subscription-extensio/nlbjncdgjeocebhnmkbbbdekmmmcbfjd>
 * <https://chrome.google.com/webstore/detail/tiny-tiny-rss-checker/injnpmieoiaflnemdibhkflicchhaldh?hl=en>

Configure both addons with the URL to the tt-rss instance
( https://feeds.fogcloud.org/ ).

For the subscription extension, you want to add a reader and enter this as your
subscription URL [1]

```
    https://feeds.fogcloud.org/public.php?op=subscribe&feed_url=%s
```

References:

 * [1] <https://tt-rss.org/oldforum/viewtopic.php?t=1334>

## Subscribe to some feeds

 * Visit <https://boingboing.net/>
 * To the right of the URL bar, you should get an RSS icon (![rss
   icon](/assets/feed-icon.svg)).
 * Click that, edit the subscription, set a category (e.g. "blogs").
 * Watch for the icon on other sites, and subscribe when appropriate.

## Android App

The official app is available for money on Google Play. No reason not to give
them money, but the app is also available through FDroid.

<https://f-droid.org/en/packages/org.fox.tttrss/>

## Uncooperative Sites

Some sites should definitely be viewed via RSS, but don't provide native
support. The site <https://fetchrss.com/> provides the ability to create RSS feeds
for some of them, e.g.:

 - Public business / group pages on Facebook
 - Youtube channels

