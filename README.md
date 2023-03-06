# Whereby Ruby HTTP API Wrapper

This gem is a very simple [Whereby](https://whereby.com) HTTP API wrapper written for Ruby/Rails projects, to easily create video meetings and conferences. 

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'whereby-ruby'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install whereby-ruby

## Usage

If using Rails put the following into an initializer. If you use plain Ruby, run this code before trying to use the API.

```ruby
require 'whereby'
Whereby.configure do |config|
  config.api_key = "Your api key!"
end
```
By default, this gem try to read the `WHEREBY_API_KEY` environment variable and use that as api key. The above statement is therefore equivalent to setting this environment variable.


### Instantiate an API object

```ruby
api = Whereby::Api.new
```

If you want to use a different API key then the default one configured as described above, you can pass an `api_key` argument to `new`:

```ruby
api = Whereby::Api.new(:api_key => "use_this_key")
```

### API Requests

```ruby
api.meeting(id)                     # GET     /v1/meetings/:id             
api.create_meeting(options)         # POST    /v1/meetings
api.delete_meeting(id)              # DELETE  /v1/meetings/:id
```
Read more about the different endpoints and options at https://whereby.dev/http-api/

### Example creating a meeting
```ruby
api.create_meeting(room_name_prefix: '/example', room_mode: "normal", start_date: "2020-08-01T00:00:00Z", end_date: "2020-08-01T15:00:00Z", fields: ["hostRoomUrl"])
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/poption/whereby-ruby.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Whereby Ruby HTTP API project's codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/whereby-ruby/blob/master/CODE_OF_CONDUCT.md).
