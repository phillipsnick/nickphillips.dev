+++
date = '2026-09-24'
draft = false
title = 'Privacy'
description = 'What this site collects, what it does not, and who else is involved.'
layout = 'simple'
+++

Short version: no accounts, no cookies, no comments, no advertising, and no
tracking that can identify you. What follows is the longer version, because
"we value your privacy" banners are how you can tell nobody does.

*Last updated: 24 September 2026.*

## Analytics

I use [Cloudflare Web Analytics](https://www.cloudflare.com/web-analytics/),
including Real User Measurements (RUM) — the part that records how quickly pages
genuinely loaded for real visitors, rather than how fast they load on my machine
on my connection. I've deliberately enabled collection for visitors in the EU
too, so the numbers describe everyone who visits instead of an arbitrary subset.

It is cookieless. It sets no identifier in your browser, cannot follow you
between websites, and builds no profile of you. What gets recorded is the page
you viewed, the site that referred you, page load timings, and coarse details
derived from the request itself — browser, operating system, and country.

I look at this to see which posts are worth writing more of, and whether
anything on the site is slow. That is genuinely the whole purpose.

## Hosting and delivery

The site is a pile of static files. It is hosted on
[GitHub Pages](https://pages.github.com) and served through
[Cloudflare](https://www.cloudflare.com). Both sit between you and the page, and
both necessarily process your IP address to deliver it and to fend off abuse.
Their handling is covered by
[GitHub's Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
and [Cloudflare's Privacy Policy](https://www.cloudflare.com/privacypolicy/).

I have no access to raw request logs from either, and I have not asked for any.

## Cookies and local storage

The site sets no cookies at all.

It does store one thing in your browser's local storage: whether you prefer the
light or dark theme. That value never leaves your device and is never sent
anywhere — it exists so the site does not flash white at you on every page load.
Clearing your browser data removes it.

## Third parties on the page

There aren't any. No embedded fonts, no CDN scripts, no social widgets, no
embedded video. Every script and stylesheet the site loads comes from the site
itself, which is why there is nothing else to disclose here.

You do not have to take my word for that. The site is open source, and
[the source for this page and everything else](https://github.com/phillipsnick/nickphillips.dev)
is on GitHub. If you find something that contradicts this page, I would rather
hear about it than not.

Posts do link out to other sites. Once you follow one of those links you are on
someone else's property and their privacy policy applies, not this one.

## RSS

The [feed](/index.xml) is a static file like everything else. Subscribing to it
tells me nothing about you — I cannot see who has subscribed, and there is no
tracking pixel in it.

## Your rights

If you are in the UK or EU, the GDPR gives you the right to see, correct, or
delete the personal data an organisation holds about you. In this case the
honest answer is that there is nothing to hand over: the analytics are
anonymous by design and cannot be traced back to an individual, so there is no
record of *you* for me to look up.

## Getting in touch

Questions about any of this, or about something I have got wrong, are welcome —
contact details are on the [about page](/about/).

## Changes

If any of this changes, I will update this page and the date at the top of it.
