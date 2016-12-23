Spree AMS
========

[![Build Status](https://travis-ci.org/hhff/spree_ams.svg)](https://travis-ci.org/hhff/spree_ams)
[![Dependency Status](https://gemnasium.com/hhff/spree_ams.svg)](https://gemnasium.com/hhff/spree_ams)
[![Code Climate](https://codeclimate.com/github/vinsol/spree_ams/badges/gpa.svg)](https://codeclimate.com/github/vinsol/spree_ams)

Spree AMS is a module namspaced under Spree's Api module, providing a Spree Application with a collection of routes that behave identically to the regular api routes, but instead respond with serialized models (via the [Active Model Serializers](https://github.com/rails-api/active_model_serializers) gem).

> This gem does not modify Spree's existing API - it can be used alongside this gem. However, its response is different from `spree_api`. Instead of sending the association objects nested within the parent object, this gem sends them at the root of serialized object. See this for more information on `embed` options of ActiveModel::Serializer : http://www.rubydoc.info/gems/active_model_serializers/0.8.2/ActiveModel/Serializer.embed.


Installation
------------

Add `spree_ams` to your Spree store's Gemfile:

```ruby
gem 'spree_ams', github: 'vinsol/spree_ams', branch: '3-1-stable'
```

If you'd like to explicitly set the host URL for the Image Serializer to output absolute URLs  you'll need to set a config.action_controller.asset_host in your Rails environment configuration.

i.e. for your `development` environment in `config/environments/development.rb` set

```
config.action_controller.asset_host = 'http://localhost:3000'
```

If you're using S3, Paperclip will take care of this for you.

Install the Initializer:


```ruby
rails g spree:api:ams:install
```

Then run ```bundle``` and you're good to go!

CORS Restrictions
-------

If you happen to use `spree_ams` for developing a seperate front end application, you'll need to set proper headers so the browsers can allow the cross origin requests. To do this, open `config/initializers/spree_ams.rb` in your editor:

```ruby
  config.cors_whitelist = 'http://localhost:4200'
```

Set this to whatever address your FE server is running on. Remember to restart your rails server after making this change.


Testing
-------

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle
bundle exec rake
```

Contributing
------------

Generate docs from the Acceptance Tests (you'll need to generate your dummy test_app first)!

```ruby
rake app:docs:generate
```


1. Fork It
2. Clone it.
3. Create your feature branch (`git checkout -b my-new-feature`)
4. Commit your changes (`git commit -am 'Add my feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request


Copyright (c) 2014 Hugh Francis, released under the New BSD License
