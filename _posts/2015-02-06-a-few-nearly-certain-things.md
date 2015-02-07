---
layout: post
title: "You'll Almost Always Do These Steps"
tags: rails web-app mvc bootstrap responsive
---

Just a quick re-cap on MVC:

### MVC
So how does a web app work anyways?  Basically, your *model* is your data.
Your *view* is what the user sees.  And your *controller* controls your data,
both from your web app to your view (what your user sees and interacts with) and
from your view to your model. MVC.


### The Rails App Recipe
In almost every project you are going to want to do a few things.  Namely:

1. [Application.html.haml](#1)
2. [Forms](#2)
3. [User model](#3)
4. [Rake commands](#4)

### <a name='1'></a>Application.html.haml
Want to use bootstrap for responsive design?  Flat-UI for a beautifully clean webpage?
d3.js? Google plugins?

Some of these things you can add as gems, but more often than not it is easiest to add
these things in your `app/views/layouts/application.html.haml` file.  This file contains the
code that will be run in every page of your application.  Near the top of this file (it should
have been generated automatically when you ran `rails new`) you should be able to add files like this:

{% highlight ruby %}
  = stylesheet_link_tag    'https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css'
  = stylesheet_link_tag    'http://fonts.googleapis.com/css?family=Lato'
  = stylesheet_link_tag    'https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css'
  = stylesheet_link_tag    'application', media: 'all'
  = javascript_include_tag 'https://maps.googleapis.com/maps/api/js?sensor=false'
  = javascript_include_tag 'application'
  = javascript_include_tag 'https://maxcdn.bootstrapcdn.com/bootstrap/3.3.0/js/bootstrap.min.js'
  {% endhighlight %}

Do you see the `= yield` part of this file?  This is where the rest of your views will be rendered!  You can
add a footer and a header on application.html.haml that will persist across all pages of your app.  More on
that later.

### <a name='2'></a>Using forms
Forms allow users to input data to your webapp.  This may be as simple as entering an email address to super
complicated date, dropdown, radio button, etc. forms.  Simple form is a great tool for using forms in
Rails.  You can install it with bootstrap responsiveness using this command: `rails g simple_form:install --bootstrap.`

### <a name='3'></a>User model
You'll probably want to keep track of your users.  To create a user model we need to run a Rails *migration*.  But before
we get to migrations, let's talk about models a bit more.  Remember, models are the data in your app.  Generally, a model
will correspond to a database table.  So, when we are determing our models, we need to determine what attributes we want
to keep track of on our database table and if we would like to restrict any of these attributes.  Let's create a simple User
model where we only want to keep track of the user's email address.  We will run `Rails g model User email:string`.  Which says 'Rails,
generate a model called User that has a property of email, which is a string.'  This command will generate a *migration* file,
modify our schema.db, and create a file as `app/models/user.rb`

Here's a bit of bonus information.  Let's say we want to have a page that lists all of our users.  This means we want to
have an *index* of our User model.  We need a User controller, index action.  Rails can create this for us, too!  We should run
`Rails g controller User index`.  Which says 'Rails generate a controller called User that has the action index.'  We will get
a route in the `config/routes.rb` and file `app/controllers/users_controller.rb`.  **Note that the model is singular (User) while
the controller (Users Controller) is plural.**

### <a name='4'></a>Rake Commands
After you run a migration, you'll need to tell your database to use it.  You should run `rake db:migrate`.  A few other commands
you might find useful:

* `rake db:drop` - drop the database.
* `rake db:create` - create the database. You'll need to do this if you want to use postgres in development.
* `rake db:seed` - seed the database with fake data.



