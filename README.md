# Anchored

Ruby auto-linking of only URLs, with no HTML sanitization.

Copied from https://github.com/tenderlove/rails_autolink.

## Install

Add to your Gemfile:

```ruby
gem "anchored"
```

Or:

```sh
$ gem install anchored
```

## Usage

```
require "anchored"

Anchored::Linker.auto_link("text")
=> "text"

Anchored::Linker.auto_link("hello www.google.com.")
=> "hello <a href='http://www.google.com'>www.google.com</a>."

text = "Welcome to http://www.dogedogedoge.com/."
Anchored::Linker.auto_link(text, target: "_blank") do |text|
  text[0...12] + "..."
end
# => "Welcome to <a href=\"http://www.dogedogedoge.com/\" target=\"_blank\">http://dogedo...</a>.
```

Anchored does not sanitize html. Be sure to use something else for that.

## Differences from `rails_autolink`

* No HTML sanitization
* No email auto-linking
* No dependencies on rails
* Dropped support for uncommon protocols (gopher, etc)

## Development

Run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. 

You can also run `bin/console` for an irb prompt that will allow you to experiment.
 

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/neighborland/anchored. 
This project is intended to be a safe, welcoming space for collaboration, and contributors 
are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
