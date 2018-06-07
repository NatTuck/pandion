---
layout: post
title: "You, Personally, Should Stop Using Facebook"
date: 2018-06-07 15:30
comments: false
categories:
---

When you use Facebook, instead of sharing posts with your friends, you share
them with Facebook who then redistributes the posts for you. You have no privacy
from Facebook in whatever part of your life happens there.

That's bad, but that's not the whole problem.

By chosing to use Facebook as your method to share things with your friends,
you're compelling them to use Facebook too. If they don't log in, they'll miss
out on what you post. If Facebook is your only social communication tool, then
if they don't use it you won't see their messages.

By using Facebook, you're not just giving up your own privacy. You're pushing
all your friends and relatives to give up their privacy if they want to
communicate with you.

That's bad, but that's not the whole problem.

Facebook makes money on advertising. When you scroll through your Facebook feed,
you're not just seeing posts from your friends - you see sponsored content as
well. Your relative just got married, your friend is angry about politics, and
Dollar Shave Club sells great razors - all part of the feed.

You might not be bothered by advertisements for razors in your social
communication service, but again - it's not just you. By using Facebook, you're
saying that your friends get your posts with ads on them.

This is much worse than it sounds.

Ads, in general, aren't harmless. See [Hank Green's video on
Youtube](https://www.youtube.com/watch?v=CC3OOXD_2MA) about dealing with
advertisements for causes he doesn't support showing up in front of videos on
the channels he manages. Youtube channels have some control over which ads they
show, but on Facebook you have no control over what ads show up with your posts.

## Targeted Advertising

Modern advertising on the Internet is a pretty serious business. It's not just
about showing the same ad to everyone. It's about figuring out who's going to be
most vulnerable to influence and showing them the exact right ad at the exact
right time.

In order to do that, companies like Facebook and Google build up a personalized
profile - or "data ghost" - for every user. This isn't just limited to people
who have intentionally signed up for services from these companies, but signing
up for the service helps. 

Your data ghost is a digital model intended to let advertisers figure out pretty
much evertying about you, and even to predict your future actions. This isn't
perfect... but the old story about [Target knowing a teenager was pregnant
before her
dad](https://www.forbes.com/sites/kashmirhill/2012/02/16/how-target-figured-out-a-teen-girl-was-pregnant-before-her-father-did/#228f7f966668)
happened back in 2012, and this sort of technology doesn't get worse over time.

Here's where it gets scary.

Facebook doesn't show you all of the posts your friends make, nor does it show
you posts in the order they happened. Instead, posts are algorithmically
selected to maximize the time you spend on Facebook and to maximize the impact
of the advertisements that are shown.

Facebook posts may or may not communicate with your friends - your friends may
never see them - but they do give Facebook more content to use for targetted
personalization.

As an example of what can be done with this sort of system, Facebook did an
experiment in 2014 where they [manipulated people's feed to get them to
vote](https://www.vox.com/2014/11/4/7154641/midterm-elections-2014-voted-facebook-friends-vote-polls).
This experiment was probably harmless - they just got random extra people to
vote - but your data ghost can tell them how you're going to vote before they
decide whether to encourage you.

## Cambridge Analytica

Cambridge Analytica was a political PR firm that used a wide variety of data -
including Facebook data - to build data ghosts for use by political compaigns. They
were hired to promote political issues like Brexit and political candidates like
[Donald
Trump](https://www.theguardian.com/news/2018/mar/17/cambridge-analytica-facebook-influence-us-election).
There's a [list of other
clients](https://en.wikipedia.org/wiki/Cambridge_Analytica#United_States) on
Wikipedia.

One mechanism they used for collecting data was a Facebook app.

> Only 270,000 Facebook users actually installed the app, but due to Facebook's
> data sharing policies at the time, the app was able to gather data on millions
> of their friends.

Of course, once they had collected personal data and built data ghosts, they
used targeted advertising on Facebook and other services to influence political
elections for their clients.

[They aren't alone](https://www.washingtonpost.com/business/economy/facebooks-rules-for-accessing-user-data-lured-more-than-just-cambridge-analytica/2018/03/19/31f6979c-658e-43d6-a71f-afdd8bf1308b_story.html). 
Most accounts 
[have been scraped](http://www.businessinsider.com/facebook-87-million-cambridge-analytica-data-2018-4)
by third parties. Any developer using the Facebook API (e.g. any time you've
clicked a "log in with Facebook" button - like for a quiz) has access to not just
your profile data, but some of your access to your friend's data.

Further, this issue isn't just with Facebook. Any centralized social network can make
money selling your data ghost. [Twitter was another Cambridge Analytica data
source](https://9to5mac.com/2018/04/30/cambridge-analytica-twitter/).

## The Problem

By using Facebook, you are compelling your friends and family to to use an
information delivery system specifically designed to use your posts to
manipulate their behavior. At best, it's manipulating them to buy things they
don't need. At worst, it's trying to influence their political actions and
positions. This may be at the bidding of Facebook themselves, or anyone who buys
the service.

You, Personally, Should Stop Using Facebook.

## Federated Social Networking

The main reason I didn't post this sooner is that there wasn't any plausible
replacement to suggest. 

**Switching to a similar service like MySpace or Google Plus won't help.** They
have the same personalized-advertisement model as Facebook, with all the same
problems. Google, especially, is even worse - they have more data about you, so
the data ghosts they build are more dangerous.

Luckily, the World Wide Web standard body recently published a standard called
ActivityPub. This protocol allows a bunch of different social networking servers
to interoperate, so there can be a bunch of small social networks rather than
one big one. This works kind of like email, where someone on AOL can email
someone on Compuserve.

There are now several different computer programs that implement this standard,
and a large number of people running small social networking servers for the
good of the community. This whole thing is called the Federated Social Network
Universe, or the "Fedverse". This replaces a company trying to build and sell
your data ghost with an arbitrary person volunteering to build a community.

The result is more like Twitter than Facebook, and the resulting network isn't
mature, but it largely works and is growing. 

To get started, go to [Join Mastodon](https://joinmastodon.org/).

If you're interested in excess technical detail about software alternatives, a
good place to start is [fedverse.network](https://fediverse.network/) and
[here](https://medium.com/we-distribute/a-quick-guide-to-the-free-network-c069309f334).

Here's [my fedverse account](https://ferrus.net/@nat).
 
## Actions to Take

 - [Set up a Mastodon account.](https://joinmastodon.org/)
 - Check out [Resources for Mastodon Newbies](https://github.com/nolanlawson/resources-for-mastodon-newbies).
 - Share your new account with your friends.
 - Uninstall the Facebook mobile app.
 - Make a post about how all your friends should move to
   the Fedverse with you.
 - Log out of Facebook, and try not to log back in.

If you can't manage to stay logged out of Facebook:

 - Use the Firefox web browser.
 - Install the [Facebook Container](https://blog.mozilla.org/blog/2018/03/27/facebook-container-add-on/) addon.

I don't recommend deleting your Facebook account. If nothing else, keeping it
makes it harder for someone to make a fake one and impersonate you.

## Other Cloud Services

Facebook isn't the only centralized communication platform that's a serious
problem. Google has [more of your
data](http://theantimedia.com/google-10-times-data/) and is much harder to get
away from.
[Amazon](https://www.theguardian.com/technology/2018/may/24/amazon-alexa-recorded-conversation),
[Apple](https://blog.usejournal.com/apple-collected-4-years-of-my-browsing-history-in-a-hidden-log-that-american-users-might-not-have-d0850a982478),
and Microsoft are also major problems. One of these companies probably controls
your email, which means they own your identity online.

Getting away from Facebook is easier than the others, and that makes it a good
start.

I plan to make one or more posts about why you should escape Google, Amazon,
Microsoft, and Apple. Hopefully I'll get around to it. Google and Amazon are
scarier than Facebook.

## More Links

The data that Facebook and others collects isn't limited to what you type into
Facebook. Facebook trackers can link your browsing on other websites to your
data ghost. Anytime you see a Facebook "Like" button, 
[Facebook sees you](https://www.cnet.com/news/facebook-like-button-draws-privacy-scrutiny/). 

Other advertisers on the same websites may be able to link their data to your Facebook account as well [through the Facebook trackers](https://techcrunch.com/2018/04/18/login-with-facebook-data-hijacked-by-javascript-trackers/).

If you have the Facebook app installed on your mobile phone, it 
[may have access to data that you have not intentionally shared with Facebook](https://www.theguardian.com/technology/2018/may/24/facebook-accused-of-conducting-mass-surveillance-through-its-apps).

Facebook has tweaked their service to look better, but their business model
depends on building and sharing your data ghost. [That hasn't
changed](https://www.nytimes.com/interactive/2018/06/03/technology/facebook-device-partners-users-friends-data.html).

Allowing this sort of targeted manipulation + filter bubble world to progress
is a 
[really bad idea](http://www.antipope.org/charlie/blog-static/2018/05/happy-21st-century.html).

[Facebook scans and may block private messages.](https://www.bloomberg.com/news/articles/2018-04-04/facebook-scans-what-you-send-to-other-people-on-messenger-app)

