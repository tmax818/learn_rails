# Learn Ruby and Rails

This is my first attempt at a Ruby/Rails tutorial. I will borrow from ... This is a record of how I got here.

```Bash
[~]$ rails new learn_rails -d postgresql
[~]$ cd learn_rails/

```

Then I generated a new controller for my static pages like so:

```Bash
[learn_rails (master)]$ rails g controller StaticPages home help about
```

This creates all kinds of crap as you can see in the terminal. To get rid of the smoke signal and create my own I need to change:

```Ruby
Rails.application.routes.draw do
  get 'static_pages/home'
  get 'static_pages/help'
  get 'static_pages/about'
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```

to this

```Ruby
Rails.application.routes.draw do
  root 'static_pages#home'
  get 'static_pages/help'
  get 'static_pages/about'
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```

# Get it on Heroku

Follow instructions [here](https://devcenter.heroku.com/articles/getting-started-with-rails5)

```Bash
[learn_rails (master)]$ heroku login
heroku: Press any key to open up the browser to login or q to exit:
Logging in... done
Logged in as tylermaxwell661@gmail.com
[learn_rails (master)]$ heroku create
Creating app... done, ⬢ frozen-everglades-18104
https://frozen-everglades-18104.herokuapp.com/ | https://git.heroku.com/
frozen-everglades-18104.git
[learn_rails (master)]$ git config --list | grep heroku
remote.heroku.url=https://git.heroku.com/frozen-everglades-18104.git
remote.heroku.fetch=+refs/heads/*:refs/remotes/heroku/*

[learn_rails (master)]$ git push heroku master

```

I am going to follow the Getting Started Guide for the sake of simplicity. Articles will be the resource used for examples.

Starting [here](https://guides.rubyonrails.org/getting_started.html#getting-up-and-running)

Modify routes.rb as follows:

```Ruby
Rails.application.routes.draw do
  root 'static_pages#home'
  get 'static_pages/help'
  get 'static_pages/about'

  resources :articles
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end

```

run `$ rails routes` to see all the CRUD routes generated. Then generate the controller `$ rails g controller Articles` I can't believe how hard it was to get erb to render and text in an erb file!
