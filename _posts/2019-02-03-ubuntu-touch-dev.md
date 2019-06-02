---
layout: post
title: "Trying to develop for Ubuntu Touch in 2019"
date: 2019-02-03 17:00
comments: false
categories:
---

My phone broke, and I decided to get myself an old phone and install Ubuntu
Touch on it. Here's the story of me trying to get an audiobook player working.

## The Setup

Canonical, the makers of the Ubuntu distro, wanted to ship Ubuntu on phones at
least as far back as 2010 when they announced their Unity desktop shell. It's a
great vision: Phones are computers, so they should run the same OS as any other
computer. There are UI differences, but that just means some work on UI design.

In 2014 they ran a croudfunding campaign on Indiegogo for the Ubuntu Edge, a
high end phone that would run the new phone variant of Ubuntu they had been
developing. They wanted to go straight from nothing to mass produciton, so they
set their croudfunding goal at $32 million. A phone that ran real GNU+Linux and
could be docked to a monitor to run desktop apps sounded great, so I put in my
$650. Then they gave me my money back when they only raised $12 million.

The Edge campaign demonstrated the basic problem with Canonical's strategy for
phones. Only 17000 pre-orders wasn't enough demand, so they cancelled the phone.
They weren't interested in distributing a low-volume product to developers and
early adopoters, instead they wanted to compete with Google and Apple day 1.
Needless to say, that was never going to work - pretty much only Apple can skip
the early adopter phase, and they can only do it by using huge piles of cash and
only some of the time.

After the Edge campaign failed, Canonical moved on to plan B: They worked to
find a manufacturer and carrier who were willing to mass produce and ship a
phone with their OS. In 2015 and 2016 and the manufacturer BQ shipped two Ubuntu
Touch devices through normal retail channels in Europe: A phone an a tablet,
both with budget-class hardware. There were also two devices that shipped in
China.

The new Ubuntu phones weren't terribly successful. As far as I can tell,
approximately nobody wanted the product as shipped.

 * People who wanted a cheap smartphone preferred Android.
   * There was no Android compatibility layer for some reason.
 * Tech enthusiasts and early adopters had no interest in a low-end phone.
 * These phones weren't made easily available as dev kits.
 * These phones weren't easily available outside of Europe and China.
 * The "convergence" story of running the same apps on desktop and phone had
   been abandoned in favor of offering a desktop mode container for when the
   device was docked.

These devices had very limited software support. An "Ubuntu Touch" application
was a completely new thing. Existing Ubuntu apps didn't work for two reasons:

 - They didn't have UI support for small touchscreens.
 - Ubuntu Touch enforced strict mobile-style application constraints that
   basically required new apps be written from scratch.

By 2017 Canonical had cancelled the Ubuntu touch project and given up on
convergence for desktop Ubuntu.

Also in 2017, Purism started a croudfunding campaign for a GNU+Linux phone, the
Librem 5. I backed this one too, and it suceeded because they set their sights
on the much more reasonable target of shipping to free software early adopters.

I had been using a OnePlus One with a Google-free ROM since 2014, and I expected
that to hold out until the Librem 5 shipped. Unfortunately, I finally broke it
in November 2018.

Fortunately, Ubuntu Touch maintence had been picked up by a community group
called ubports, and they had gotten it installable on a couple of older devices.

So I ordered a Nexus 5 for $100 and installed Ubuntu touch. And there were no
apps. The app store is mostly links to web pages that kind of work in the
sketchy old chromium-based browser.

What could I do with it?

 * It makes phone calls.
 * The camera works
 * The browser works surprisingly well
 * The email client mostly works
 * No XMPP or IRC 
 * There is a Matrix client, so that works for IM.
 * The alarm clock thought I was in UTC and went off five hours early once.
 * There's a file manager by default
 * I can ssh into it and get a bash shell, or scp files to/from my desktop
 * There's no audiobook player

## Writing an App

No audibook player?!? That's not going to work. That's like half of the reason I
carry a phone.

But this is an open source platform with open source apps and I'm a programmer.
I should be able to solve this problem.

**Mid December**

There's a media player app installed by default. An audiobook player is just a
media player that saves it's place. Fixing this should take me like two days:
One to figure out app development on this platform, and one to add timestamp
checkpointing to a fork of the media player.

So I fork the media player and try to figure out how to build it. Looks like
there's an Ubuntu SDK... that doesn't work with the current version of Ubuntu
touch. The new tool to build apps is is called "clickable", but that doesn't
build the media player.

There's a music player app on the market, but it also wasn't built with the
current dev tools. Eventually I do get one of these two apps to build an
install, but apps have a hardcoded name that appears in several places, so it'll
be easier to start a new project than to modify a fork.

**Late December**

Both of the example apps use a system component called QMediaPlayer to play
audio, which is well documented. The process to create a new app is documented.
New plan: Make a new app, use QMediaPlayer to play audio, easy times.

 - Plan: Use a file selection dialog to pick a file.
 - Problem: There are no file selection dialogs.

At this point it's time to track down the IRC channel and find out how I'm
supposed to do this. 

 - Plan: Apparently I'm supposed to find files using an API called Content Hub.
 - Problem: Apparmor permission denied.

Ubuntu Touch is like other mobile operating systems, and heavily restricts
applications on the assumption that developers are both incompetent and
malicious. Everything is disallowed by default, and some things can be
re-enabled by requesting a permission in the app manifest.

Fine. So I enabled every permission that sounded even slightly like file access
or audio playback. And the ContentHub mechanism let me pick a file. And I
couldn't actually access the file once picked. QMediaPlayer couldn't play it
from the cache directory it got copied to, and and the API to move it somewhere
else wasn't cooperating.

 - Plan: Use Content Hub
 - Problem: It's obnoxious.
 - Plan: Just put the files somewhere I can read them to begin with, and
   play them there.
 - Problem: The "play audio" permission doesn't actually let you play audio.

So QMediaPlayer will only actually play an audio file if you have the play audio
permission *and*:

 1. You are the stock MediaPlayer app. It's App ID is hardcoded.
 2. You're playing a file in your app's local data directory.

**Early January**

New plan:

 - Manually put audiobooks into a path I'm allowed to read from with the correct
   permissions: ~/Documents/Audiobooks
 - To play a file, copy it to the app data directory and then play it from there.
 - Every five seconds, store the timestamp in a file in the app data directory.
 - When the app starts, check for and restore a stored timestamp.

Problem: When the screen turns off or the user switches apps, my app gets
   SIGSTOP. Audio still plays, but the app can no longer save timestamps.

This is a power saving feature, and there's no way for the app to disable it.
Running background processes or services is intentionally prevented as well.

People have apparently been complaining about the lack of background processing
in Ubuntu Touch since [at least
2015](https://lists.launchpad.net/ubuntu-phone/msg15883.html). Without this
functionality native apps for the platform are basically useless, and yet the
developers both at Canonical and ubports have made the intentional decision to
A.) leave this functionality disabled by default and B.) not provide any
alternative mechanism.

**Mid January**

There's a tweak tool that allows the users to prevent the system from suspending
particular apps when they lose focus. This wouldn't help if I were writing an
app to be distributed in the app store, but for my personal goal of being able
to listen to audiobooks on my phone it'll work.

**End of January**

With that, I finally got a really crappy (and ugly) audiobook player working.
Now I'll have to try using it for a while and probably fix bugs. Maybe I'll
fight with the UI a bit, but QML without QT Creator isn't the most fun I've ever
had.

Here's the app if you also want to listen to audiobooks on Ubuntu touch and
enjoy want to deal with awful UX and building from source:

  - [https://gitlab.com/nattuck/bookplayer](https://gitlab.com/nattuck/bookplayer)

## Final Thoughts

The current state of app containment and platform policy makes Ubuntu Touch
effectively broken.

Personally, I hope my Ubuntu Touch phone will work as is until the Librem 5
ships, and then I hope PureOS on that will be more useful. If I have free time I
may check out Postmarket OS or Sailfish, but I won't have free time.

Suggestion for the Ubuntu Touch platform: Provide a way to fully opt-out of
containment and platform policy like app suspention. Having to make a new UI for
a new form factor is fine, but if I'm developing on an "Ubuntu" system I expect
to be able to do basic stuff like forking, writing to files in the user's home
directory, or getting the MediaPlayer service to play *any* file.

I understand the *goal* of having a capability whitelist for each app, but the
plan only really works if capabilities you need can be whitelisted. Currently,
that's not true on Ubuntu Touch.

