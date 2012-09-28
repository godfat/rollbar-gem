# Ratchetio

Ruby gem for Ratchet.io, for reporting exceptions in Rails 3 to Ratchet.io. Requires a Ratchet.io account (you can sign up for free).

## Installation

Add this line to your application's Gemfile:

    gem 'ratchetio'

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install ratchetio

Then, run the following command from your rails root:

    $ rails generate ratchetio YOUR_RATCHETIO_PROJECT_ACCESS_TOKEN

That will create the file `config/initializers/ratchetio.rb`, which holds the configuration values (currently just your access token) and is all you need to use Ratchet.io with Rails.

To confirm that it worked, run:

    $ rake ratchetio:test

This will raise an exception within a test request; if it works, you'll see a stacktrace in the console, and the exception will appear in the Ratchet.io dashboard.

## Person tracking

Ratchet will send information about the current user (called a "person" in Ratchet parlance) along with each error report, when available. This works by trying the `current_user` and `current_member` controller methods. The return value should be an object with an `id` property and, optionally, `username` and `email` properties.

If you use different naming, add the following in your controller:

```ruby
alias_method :my_user_method, :current_user
helper_method :my_user_method
```

## Help / Support

If you run into any issues, please email me at brian@ratchet.io

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
