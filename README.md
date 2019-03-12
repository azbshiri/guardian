# 💂‍Guardian
Poor man's basic authentication 

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'guardian'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install guardian

## Usage

Include `Guardian` in your specific controller or a base one

```ruby
class ApplicationController < ActionController::API
  include Guardian

  rescue_from Guardian::Unauthenticated do |error|
    render json: { error_human: error }, status: :unauthorized
  end

  rescue_from Guardian::Unauthorized do |error|
    render json: { error_human: error }, status: :forbidden
  end
end
```
And use `authenticate!` method to check whether user provided credentials

```ruby
class PetsController < ApplicationController
  before_action :authenticate!, only: %i[create update delete]

  def create
    # create a pet
  end
end
```

Done! Whoah


## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/guardian.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
