---
layout: post
title: "Testing HTTP requests in Rails with VCR"
description: "A guide to setting up the VCR gem in Rails to test HTTP requests"
tags: [ruby, rails, testing, rspec]
---

Recently I was working on a [project](https://github.com/katebeavis/pr-hero/){:target="_blank"} that relied heavily on the Github API which meant that when I was running tests, I was hitting the API everytime. Now for authenticated requests, the rate limit was set at 5,000 hits per hour - I am a believer in testing as much as you can, but I don't think even I could hit that limit!

The main issue for me however, was that I was hitting a 'live' repo (one I use at work), and trying to get back things like number of comments made on pull requests in the past 24 hours. Unfortunately, my pesky colleagues kept on doing silly things like reviewing each others PR's and making comments, so tests like this that would pass minute....

{% highlight markdown %}
it 'returns the number of comments for each user' do
  expect(compute_comment.get_comments_by_user(users)[0].count).to eq(95)
end
{% endhighlight %}

....would end up failing as soon as that user had made another comment :angry:

And, if you do happen to be using an API with a low rate limit or a paid one, or just want to speed up your RSpec tests (don't we all), you will want to find an alternative to constantly making HTTP requests.

This is where the [VCR gem](https://github.com/vcr/vcr){:target="_blank"} comes in. We use VCR at work on most of our Rails projects but I didn't really understand how it worked, and in fact thought it was really complicated to use (spoiler alert: it's not!).

# So, how does VCR work?

VCR works by letting your tests hit the API as usual the first time the test is run. It then stores the response it gets back as a 'cassette' file. From then on, everytime you run your specs, that test will use that cassette. This meant that I could ~~hack away at~~ refactor my ``get_comments_by_user`` method and if it failed, it would be because I messed something up in the code, not because somebody had made another comment.

# Sounds good, how do I set it up?<br />
### 1. Install gems

First things first, you need to add the gem to your Gemfile. You will also need to use another gem that helps to stub out external HTTP requests such as

* [WebMock](https://github.com/bblimke/webmock){:target="_blank"}
* [Typhoeus](https://github.com/typhoeus/typhoeus){:target="_blank"}
* [Faraday](https://github.com/lostisland/faraday){:target="_blank"}

I have seen some tutorials referring to FakeWeb, but please don't use that unless you like deprecation warnings :satisfied:

Add them to your Gemfile and bundle install

{% highlight markdown %}
gem 'vcr'
gem 'webmock'
{% endhighlight %}

{% highlight markdown %}
bundle install
{% endhighlight %}

### 2. Add configuration

Add a ``cassettes`` directory inside ``spec`` - this is where your cassettes will be saved

Add a new file ``vcr_setup.rb`` inside your ``spec`` directory (or you can just add this code directly to your ``spec_helper.rb``). In this file, add the following code:

{% highlight markdown %}
require 'vcr'

VCR.configure do |c|
  c.cassette_library_dir = 'spec/cassettes'
  c.hook_into :webmock
end
{% endhighlight %}

Remember to add ``require 'vcr_setup.rb'`` to your ``spec_helper.rb`` or where ever you need to so that it is required by your test suite.

## 3. Add VCR to your test

Wrap your expectation in a VCR block and name the cassette something relevant:

{% highlight markdown %}
it 'returns the number of comments for each user' do
  VCR.use_cassette('comments_on_pull_requests') do
    expect(compute_comment.get_comments_by_user(users)[0].count).to eq(95)
  end
end
{% endhighlight %}

Now when you run the test for the first time, a cassette called ``commments_on_pull_requests.yml`` will be saved in your ``spec/cassettes`` directory.

The next time you run this test, it will use this cassette. To test that it is using it, you can try turning off your Wifi and it should still pass.

## 4. Run a VCR cassette for a whole file

Instead of wrapping every test expectation in a file in a VCR block which could get very tedious, you can add the cassette to a ``before do`` block. Just don't forget to eject it afterwards:

{% highlight markdown %}
before do
  VCR.insert_cassette('comments_on_pull_requests')
end
after do
  VCR.eject_cassette
end
{% endhighlight %}

You can also use this inside multiple describe blocks, meaning that you can use multiple cassettes for blocks of tests within your spec.

## What if you don't want to use VCR for every HTTP request?

After adding VCR, if you try to run a spec that makes a HTTP request without a cassette, you will get a ``VCR::Errors::UnhandledHTTPRequestError``

{% highlight markdown %}
An HTTP request has been made that VCR does not know how to handle:
  POST https://someurl.com/
     
 There is currently no cassette in use. There are a few ways
 you can configure VCR to handle this request:
{% endhighlight %}

Either wrap that spec in a VCR block, or, if you don't want VCR to handle this request, just add the line ``c.allow_http_connections_when_no_cassette = true`` within your VCR configure block in the ``vcr_setup.rb`` file.

### A gotcha

Sometimes this error can occur even when you have a cassette in place. I have found that this tends to happen when I am including a variable in my test, like a username that is required to hit the API, and for some reason I have changed it.

In a situation like this, I usually grab this line from the error: ``POST https://someurl.com/`` and compare it the url under the ``uri`` key in the cassette that I am using for that test.

## Wrapping up

VCR is a simple to use gem that can save a lot of headaches when it comes to testing API's with RSpec, and can even speed up your test suite and let you test when you have no internet connection :tada:

I hope that you have enjoyed this post and found it useful. Please let me know if you have any questions or issues in the comments :smiley:
