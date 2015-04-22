---
layout: post
title: "A first time for open source"
description: 
headline: 
modified: 2015-04-21
category: coding
tags: [ruby, rails, open-source, coding]
comments: true
mathjax: 
---

Contributing for some open source project is one of the things I always left to
be done tomorrow/next week/never. I always admired very much people with the
iniciative to keep running the projects that I and a lot of other people use on
a daily basis, but for a mixture of insecurity about the quality of my own code
a little bunch of lazyness too, the contributions always were left on the second
plan.

Another interesting point where I think everybody that someday wanted to
contribute to open source got to is not knowing how to begin. A lot of project
include guidelines for people who want to help and 5 minutes of Google-Fu will
get you tons of videos about people who contribute to various awesome projects
talking about how they started, but it's hard to find references about the
process itself. Somebody telling all the failures and successes on the way as he
moves forward.

The main reason of making this blog is it.

About a week ago I started to send contributions. The first two were for two
[Ansible](http://www.ansible.com/home) roles which, in case you don't know, is a
system for server provisioning (an automated way of installing all the junk that
makes your apps work). They're still sitting there waiting review. A warm start.

During the week, as I was organizing stuff for the blog, I started to seach for
an open source commenting system as a Disqus alternative and even got to
thinking about making one my own untill I found [Juvia](https://github.com/phusion/juvia).

The project was not being maintained and was stalled for some months now. Taking
a look at the project I could see that the code was well organized, the tests
made sense and (for my surprise), all passed. It was still using Rails 3.2, so i
had found my mission.

*Let's give this motherfucker some love*

My final objective was letting it working with Rails 4.2 and Ruby 2.2 with all
tests still working.

The first thing I did was changing everything to the last version and from there
start fixing things, which turned out to be a bad move.

Everything broke and half an hour later I realized that it was not the way to
go, so I came back to Ruby 1.9.3, and Rails 4.0 and used the 
[Rails Upgrade Guide](http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html) to
adjust thing *the right way* and once everything passed again, I went to Rails
4.1 and so it goes.

Some of the interesting things I learned about in the process:

- Using `object.method(:method_name).source_location` will save you A LOT of
  time debugging, specially where it's not your code you're fiddling with (i
  actually knew this already, but used it very much in the process).
- [Capybara Screenshot](https://github.com/mattheworiordan/capybara-screenshot)
  will do the same for your when you're dealing with integration tests with
  javascript enabled.
- Using [Transpec](http://yujinakayama.me/transpec/) to convert your old [Rspec](http://rspec.info/)
  specs to the Rspec 3.0 expect syntax works like a charm.
- When you're serializing json that contains html tags in rails post 3.2, the
  '<' and '>' characters will be converted to their utf-8 hex representation.
  There was a test failing because of this and I thought it was a bug in the json
  parser but turns out it makes a lot of sense. This way, some guy cannot inject a
  script tag with malicious code in your json.

Everything done, I sent the pull request and thought it would be sitting in pull
request limbo just like the others, but for my surprise, it was merged in the
next morning and I even got an email of the repo owner thanking me for the job.
The feeling was pretty awesome.

He was even thoughfull in alerting that I placed Devise secret key in version
control and fixed it after doing the merge.

And [here's the little bastard](https://github.com/phusion/juvia/pull/67).

If you find any problems, be sure to scream at me and open an issue.
