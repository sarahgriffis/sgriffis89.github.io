---
layout: post
title: "Models, and Views, and Controllers! Oh My!"
tags: rails web-app mvc
---

### MVC
So how does a web app work anyways?  Basically, your *model* is your data.
Your *view* is what the user sees.  And your *controller* controls your data,
both from your web app to your view (what your user sees and interacts with) and
from your view to your model. MVC.

### Homepage Controller
After you've run [Rails new]({% post_url 2015-01-30-web-app-101 %}), try to run
`rails s` on the command line from the directory of your app.  Then navigate to
`http://localhost:3000/` in your browser.  You'll see an error.  This is because
we haven't told our app the *route* of our home page; that is, we need to tell our
app what the first controller action should do. Here are the steps to step up your homepage:

* In **config/routes**, create a root_path.  E.g., `root 'welcome#index'`.  This will route
our homepage to the welcome controller, index action.
* In your **app/views** folder, create a **welcome** folder and a **index.html.haml** file.
The welcome folder will host the view for the welcome controller.  The index.html.haml file
will host all of the homepage content.
* You can write standard HTML in the haml file, but haml also has some amazing capabilities
to interact with ruby.  [Haml](http://haml.info/) is awesome!
* Run `rails s` from the command line and go to localhost:3000. Do you see the content from
the index.html.haml file?!


