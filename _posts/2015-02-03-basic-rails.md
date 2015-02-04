---
layout: post
title: "Choosing Gems"
tags: rails web-app gems
---

If you are familiar with any other programming language, you've probably come
across the notion of packages (R), SSCs (STATA), or modules (Python). In Ruby, we
have [*Gems*](https://rubygems.org/).

You control which gems are added to your Rails app by added them to you Gemfile.
Keep in mind you might want to keep some Gems out of your production environment, like
debugging Gems such as pry-rails. Here's a snippet of my Gemfile:

{% highlight ruby %}
group :production do
  gem 'unicorn'
  gem 'rails_12factor'
  gem 'newrelic_rpm'
  gem 'raygun4ruby'
end

group :development do
  gem 'spring'
  gem 'better_errors'
  gem 'awesome_print'
  end
{% endhighlight %}

I highly recommend the [better_errors](https://github.com/charliesome/better_errors) Gem; it makes debugging a breeze with helpful out and
a console to work directly from on the page.

![better_errors]({{ site.url }}/assets/better_errors.jpg)

You can find Gems to handle pagination, votability, APIs, and a ton of other helpful things.
A few of my production Gems are needed for hosting a web app on Heroku, more on this later!
