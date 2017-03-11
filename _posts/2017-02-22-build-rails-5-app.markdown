---
layout: post
title: "Practical Rails 5 App In One Hour – Part 1"
date: 2017-02-22 06:25
permalink: build-rails-app.html
keywords: "practical rails 5 app, rails 5 examples, rails 5 tutorials"
excerpt: "Let’s discuss the five practical Ruby on Rails projects you’ll ever be tasked to build, plus the stack and Ruby libraries you could use to speed up your development process."
author: rkcudjoe
image: 'images/rails_app.png'
---

There’s no better way to learn a new programming language, framework or skill than to apply what you’ve studied to practical projects. However, it can be difficult to find commercial projects you can work on to improve your Ruby on Rails skills.

It's likely you’ve postponed building something tangible that you can show off to your friends and potential employers because everything becomes a slog after you’ve learned the basics of Ruby and Rails.

Instead, you end up reading every tutorial about the latest Ruby gems and SQL optimization techniques, making things even more complex.

If you’ve taken Ruby on Rails courses, read dozens of books, and still feel like you need to memorize the core Ruby classes before you can call yourself a Rails developer, you’ll be pleased to know that there are just five ways to use your new found skills and knowledge.

When you’re hired as a Rails developer to create value for both offline and online businesses, there are five possible ways to achieve that. Let’s discuss the five practical Ruby on Rails projects you’ll ever be tasked to build, the stack you could use plus gems you could use to speed up your development process.

#### **You can use Rails to build brochure sites.**

Businesses have used brochures to present themselves in various situations to prospective buyers since printers were invented. Salespeople leave them behind after a visit with a prospective buyer, send them through the mail or stuck them under windshield wipers to show their products and services.

The most important thing that a brochure accomplishes is convince people to contact the company about their offerings. While paper brochures are limited to six panels, you can use Rails to build brochure sites with pages of information for prospective buyers to explore.

Brochure sites aren’t good at generating leads and sales for businesses, but they do a fantastic job of supporting salespeople, who can refer prospects to it to learn more about products and services. You’ll also build brochure sites to provide contact information about a company, help visitors find the location of physical stores, and establish a company’s brand image.

#### **You can use Rails to build publication sites.**

A typical publication site offers original and curated information for prospects and customers to consume. Examples of publication sites include Mashable, Youtube and Code School. If you’ve ever built a blog with Rails, you’re already familiar with how publication sites work.

They provide content in a variety of formats and media, such as text, video and audio.
The goods for sale on publication sites are either original or curated online content, and they make money through subscriptions, donations, and advertisements.

#### **You can use Rails to build online stores (ecommerce).**

Amazon, Etsy, eBay, information marketers and book authors use online stores to sell one or more products. Online stores (or Ecommerce sites) allow visitors to purchase a product, using any agreed-upon currency.

Online stores are different from publication sites and SaaS apps in that they don’t provide the product or service directly. Instead, you’d either download a digital product from an online store or get a physical product shipped to you after your purchase.

#### **You can use Rails to build consultative sites.**

Consultative sites are built to support salespeople through long business-to-business sales cycles. They help prospective buyers educate themselves about the problems they have and the solutions available to them until they are ready to make a purchase decision.

You’ll build a consultative site for a company that delivers complex or expensive products and services. When multiple people are involved in the decision to purchase a product or service, you’ll need a consultative site.

Your primary goal when building a consultative site is to provide guidance because it may take several days, weeks or months to sell complex offers.

#### **You can use Rails to build online services (SaaS apps).**

Applications like Pivotal Tracker, GitHub, and Basecamp were once delivered through desktop software only, but they’ve been replaced by online services you can access in your favorite browser.

Today, you can manage your finances, socialize with friends and family, organize your project ideas, and communicate with your teammates from the comfort of your browser.

Rails is a perfect framework for building these kinds of online services (or SaaS apps) in almost every industry. An online service could be used by just a company’s employees or could be productized and made available to other businesses to purchase. In either case, you’re delivering a product with the online service and customers must be granted access before they can use the product.

#### **Choose Your Customer Creation Formula**

If you're familiar with Brian Massey’s book, _Your Customer Creation Equation_, will recognize the practical Rails projects discussed in this article as customer creation formulas. When building a Rails application for your client or for your own business, you’ll choose the right combination of formulas to help get more leads, triers or customers.

The right combination will depend on how the business makes money. That means for one client, you might build an online store and a publication site, and for another, you might build a SaaS app and a brochure site. Regardless of how you use Rails, you must implement specific features to turn your coffee and code into an asset.

Now, let me show you how to build Ruby on Rails applications that don’t suck.

#### **Choose Your Default Rails 5 Stack**

One of the main reasons why Rails gained traction quickly is due to the default stack. New developers don’t have to make major decisions about what to include in their application’s infrastructure. That makes it easy to ship useful applications quickly.

However, as you gain experience with the framework and become more knowledgeable about what makes web applications stand the test of time, you find yourself making substitutions and additions.

For instance, Rails comes with MiniTest for testing, but you substitute that for RSpec because you can recite all the RSpec matchers in your sleep and everyone on your team already uses RSpec.

Which means you don’t have to worry about someone breaking stuff because they don’t understand what your tests are doing. And the fact that you can compliment RSpec with Shoulda-Matchers makes it a no brainer to stick to what you already know.

After shipping a few applications, you realize that you always include the same gems as part of your set up process, even before you start working on the core functionality of the application.

Eventually you become frustrated with your setup process because you keep doing the same thing over and over. Although you prefer your application a certain way, you can’t stand spending an entire day making things just right before you get to the fun part.

In the name of productivity, you start looking for a better way to bootstrap new Rails applications.

You can set up your Rails app the same way every time [using a template](http://everydayrails.com/2011/02/28/rails-3-application-templates.html) that meets only your preferences. Or you can learn to use another stack that’s not an exact match for your preferences, but good enough to get the job done with minor tweaks.

I prefer to use [Suspenders](https://github.com/thoughtbot/suspenders) to bootstrap new Rails applications instead of creating my own template mainly because it’s maintained by a team that’s well respected in the Rails community.

You don’t need any convincing that using Suspenders is better than creating and maintaining your own template once you take a look at Suspenders’ Gemfile and README.

Before I started using Suspenders, it never occurred to me that I needed a staging environment. I’d just deploy the application into production after completing a major feature, only to find that something that worked on my machine doesn’t work in production.

Since I started using a staging environment, I always get a chance to fix things before the end users are exposed to the application.

Additionally, Suspenders comes with Dotenv for loading environment variables, which prevents you from accidentally exposing credentials for external services; you also get Web Console for better debugging via an in-browser IRB console; all of which are already configured and ready to go when you generate a new Rails app with Suspenders.

I’d bet none of the tutorials you completed while learning Rails mentioned the importance of integrating analytics tools into every Rails apps you work on. I didn’t think about that until I saw Segment listed as one of the goodies included in Suspenders.

Of course Suspenders has more to it than the things I’ve mentioned above. But I wanted to highlight those because they are the things I initially overlooked when learning and working with Rails.

#### **Getting started with Suspenders**

You can run ``gem install suspenders`` to install the gem or ``gem update suspenders`` to grab the latest version if you have an older one.

I already have an older version installed, so I’ll update and then delete the previous one.

{% highlight  bash %}

localhost% gem update suspenders
Updating installed gems
Updating suspenders
Fetching: suspenders-1.25.0.gem (100%)
...
Gems updated: suspenders
localhost% gem uninstall suspenders

Select gem to uninstall:
 1. suspenders-1.21.0
 2. suspenders-1.25.0
 3. All versions
> 1
Successfully uninstalled suspenders-1.21.0

{% endhighlight %}

Now choose a name for your project, then run ``suspenders projectname``. That will create a Rails app in ``projectname``

{% highlight bash %}
localhost% suspenders messenger
create
create  README.md
create  Rakefile
create  config.ru
create  .gitignore
create  Gemfile
create  app
...
create  .ruby-version
run  bundle install
Fetching gem metadata from https://rubygems.org/.........
Fetching version metadata from https://rubygems.org/..
Resolving dependencies...
....
append  Rakefile
Congratulations! You just pulled our suspenders.
{% endhighlight %}
You’ll most likely have a problem with connecting to PostgresSQL during the creation of your Rails app; make sure you have PostgresSQL installed and running.

Even then, you still need to provide a username and password for connecting to Postgres, otherwise ``db:create`` won’t work.

We can use Dotenv to supply those credentials, along with a secret token.

{% highlight bash %}
localhost% cd ./messenger
localhost% touch .env.development
localhost% rake secret
{% endhighlight %}

Open ``.env.development`` and add your configuration.

{% highlight ruby linenos %}
#.env.development
SECRET_KEY_BASE="ea9d0bb08026b291630018ad7ee61f8ca277590302abf424bae835b27fe7ae9da776a4f59aadb5df47438a32d67ee362409a22abf4c575e1e9248f51a08061c2"
DB_USERNAME=rkcudjoe
DB_PASSWORD=devrkcudjoe
{% endhighlight %}

Then update ``database.yml`` with your password and username as such:

{% highlight ruby %}
#config/database.yml
...
username: <%= ENV["DB_USERNAME"] %>
password: <%= ENV["DB_PASSWORD"] %>
{% endhighlight %}

Now, create your developement and test databases, run a migration for ``delayed_job`` and restart your server. You should see the Rails welcome page on port 5000 after that.

{% highlight bash %}
localhost% rake db:create:all
localhost% rake db:migrate
localhost% foreman start
{% endhighlight %}

Now that you've setup your Rails 5 stack, why don't you go ahead and move on to part two where you'll [**build a practical Rails 5 app, using Suspenders stack and other useful Ruby and Rails gems.**](/rails-with-suspenders.html)