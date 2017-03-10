---
layout: post
title: "Practical Rails 5 App In One Hour – Part 2"
date: 2017-03-01 06:25
permalink: rails-with-suspenders.html
keywords: "practical rails 5 app, rails 5 examples, rails 5 tutorials"
excerpt: "You've already setup a default Rails 5 application so let's go ahead and add a unique feature to your application, and release your first web app in 1 hour or less."
author: rkcudjoe
image: 'images/rails_app.png'
---

I've already shown you the only five types of applications you'll ever be tasked to build when you're hired to create value as Ruby and Rails developer. You'll choose a combination of these **customer creation formulas** to build an application that meets your business goals... 

1. You can use Rails to build brochure sites
2. You can use Rails to build publication sites
3. You can use Rails to build online stores (ecommerce)
4. You can use Rails to build consultative sites
5. You can use Rails to build online services (SaaS apps)

[In part one of Practical Rails 5 App In One Hour](/build-rails-app.html), you setup a default Rails 5 application so let's go ahead and add a unique feature.

#### **Getting Started With Rails 5**

After you have cloned this repo, run this setup script to set up your machine
with the necessary dependencies to run and test this app:

	% git clone git@github.com:HookOps/hubstaff-rails.git
	% ./bin/setup

<br>

It assumes you have a machine equipped with Ruby, Postgres, etc. If not, set up
your machine with [this script].

[this script]: https://github.com/thoughtbot/laptop

After setting up, you can run the application using [Heroku Local]:

    % heroku local

[Heroku Local]: https://devcenter.heroku.com/articles/heroku-local

<br>

<script src="http://monkeyplayr.com/playr.php?u=865&p=8589"></script>

<br>

#### **Using a Ruby API client**

**Step 1:** Add `hubstaff-ruby` to your Gemfile and `bundle install`.

{% highlight ruby %}
#Gemfile

gem "hubstaff-ruby", git: "https://github.com/hookops/hubstaff-ruby.git"
{% endhighlight %}

**Step 2:** Get your [HUBSTAFF_APP_TOKEN](https://developer.hubstaff.com/my_apps), and add it to your to your `.env` file.

**Step 3:** Require files from the `hubstaff-ruby` gem in your Rails environment; before you initialize
the Rails application. And then load your environment variables.

{% highlight ruby %}
#environment.rb
...
require "hubstaff"
Dotenv.load(".env")
Rails.application.initialize!
{% endhighlight %}

**Step 4:** Define your routes to handle authentication and
retrieving data from Hubstaff.

{% highlight ruby %}
#routes.rb
get "/pages/integration" => "pages#integration" #hubstaff email/password form
post "/pages/integration" => "pages#integration", as: :integration #process email/password

get "/pages/screenshots" => "pages#screenshots", as: :screenshots #display screenshots
get "/pages/activities" => "pages#activities", as: :activities #display activities
{% endhighlight %}

**Step 5:** Define actions in your pages controller.

{% highlight ruby %}
#pages_controller.rb

include Hubstaff
HUBSTAFF_CLIENT = Hubstaff::Client.new(ENV["HUBSTAFF_APP_TOKEN"])

def integration
  if params[:hubstaff_email].present? && params[:hubstaff_password].present? #check if hubstaff email/password is submitted and grab it on post request
    @hubstaff_email = params[:hubstaff_email]
    @hubstaff_password = params[:hubstaff_password]
    authenticate_and_save_auth_token(@hubstaff_email,@hubstaff_password) #then authenticate and save the auth_token
    redirect_to root_path, notice: "Successfully Connected To Hubstaff"
  else
    render :integration, alert: "Unable To Connect To Hubstaff"
  end
end

def authenticate_and_save_auth_token(email,password)
  client_user = User.find_by_email(current_user.email)
  HUBSTAFF_CLIENT.authenticate(@hubstaff_email,@hubstaff_password)
  client_user.hubstaff_auth_token = HUBSTAFF_CLIENT.auth_token #you'll need a migration to add hubstaff_auth_token to User model
  client_user.save!
end

def screenshots #retrieve screenshots for display in your app
  if current_user.hubstaff_auth_token.present?
    HUBSTAFF_CLIENT.auth_token = current_user.hubstaff_auth_token
    @hubstaff_screenshots = HUBSTAFF_CLIENT.screenshots("2016-09-29","2016-10-01", projects: "112761")
    render :screenshots
  else
    render :integration, alert: "Please Connect To Hubstaff"
  end
end

def activities #retrieve activities for display in your app
  if current_user.hubstaff_auth_token.present?
    HUBSTAFF_CLIENT.auth_token = current_user.hubstaff_auth_token
    @hubstaff_activities = HUBSTAFF_CLIENT.activities("2016-09-29","2016-10-01",users: "61188")
    render :activities
  else
    render :integration, alert: "Please Connect To Hubstaff"
  end
end
{% endhighlight %}

**Step 6: [Your Turn]** Create forms that your users can pass the
required parameters into, so that they retrieve & display the exact data they
want.

#### **Guidelines**

Use the following guides for getting things done, programming well, and
programming in style.

* [Protocol](http://github.com/thoughtbot/guides/blob/master/protocol)
* [Best Practices](http://github.com/thoughtbot/guides/blob/master/best-practices)
* [Style](http://github.com/thoughtbot/guides/blob/master/style)

#### **Deploying**

If you have previously run the `./bin/setup` script,
you can deploy to staging and production with:

{% highlight bash %}
    $ ./bin/deploy staging
    $ ./bin/deploy production
{% endhighlight %}

#### **BONUS: Useful Ruby gems every Rails developer should know.**

There are several Rails gems that will make you an extremely productive Rails developer and help you produce high quality code. These [11 Rails libraries](https://infinum.co/the-capsized-eight/articles/a-gem-for-every-occasion-11-great-ruby-libraries-we-use-on-every-project) and other alternatives are useful for every occasion.

In order to help stakeholders make better business decisions and get a good ROI from the software you build, you must implement analytics, onboarding, and marketing automation as well.

For analytics, Segment.io gives you the ability to aggregate data from several analytics providers, including Mixpanel and Google Analytics. You can [create an analytics facade](https://robots.thoughtbot.com/segment-io-and-ruby) to pass data to Segment.io and track every user interaction in your Rails app.

You can’t just deliver a project and expect users to know how to use it on their first encounter. To improve engagement, user adoption and retention rates, you need personalized onboarding flows.

You can  provide a better onboarding experience in your Rails app with [Appcues](https://github.com/appcues/appcues-rails).

If your Rails app is for internal use only, you don’t have to worry about marketing automation at all. When you’re working on a project that’s meant for consumers, you must implement marketing automation because the number one problem product creators face is distribution.

The three primary ways to implement marketing automation and help your business reach more potential customers is through social sharing, email marketing and built-in referrals. Integrating social sharing is easy; you can use [shareable](https://github.com/hermango/shareable) or any other social sharing Rails gem. 

There are several options for transactional emails in Rails, but I’d recommend you take a good look at those that allow you to send behavior-based messages. [Drip](https://github.com/DripEmail/drip-ruby),  [Customer.io](https://github.com/customerio/customerio-ruby) and [Intercom](https://github.com/intercom/intercom-rails) are good options for email marketing automation in your Rails app. 

Getting your current customers to refer others to you is a great way to grow your online business. It’s easy to implement referral marketing with Ambassador, but that’s a little pricy. Alternatives for baking referrals into your Rails app include [Rack Affiliates](https://github.com/alexlevin/rack-affiliates) and [DeviseInvitable](https://github.com/scambra/devise_invitable). 

Obviously, you can’t do business online without a way to accept payments. To accept payments with Stripe, you can use [Payola](https://github.com/peterkeen/payola) or [Koudoku](https://github.com/andrewculver/koudoku).

There's still more to learn, but now that you've familiarize yourself with with Ruby and Rails, [**use this 2-step backdoor strategy to jumpstart your web development career**](/jumpstart-dev-career.html), even before you master Ruby and Rails topics, concepts and techniques.