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
