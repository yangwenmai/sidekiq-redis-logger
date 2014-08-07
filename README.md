# Sidekiq::Redis::Logger

TODO: Write a gem description

## Installation

Add this line to your application's Gemfile:

    gem 'sidekiq-redis-logger'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install sidekiq-redis-logger

## Usage

TODO: Write usage instructions here

**sinatra**

> 
# initialize log
require 'logger'
Dir.mkdir('log') unless File.exist?('log')
class ::Logger; alias_method :write, :<<; end
case ENV["RACK_ENV"]
when "production"
  logger = ::Logger.new("log/production.log")
  logger.level = ::Logger::DEBUG
when "development"
  logger = ::Logger.new(STDOUT)
  logger.level = ::Logger::DEBUG
else
  logger = ::Logger.new("/dev/null")
end

> 
# initialize Redis
case ENV["RACK_ENV"]
when "production"
  REDIS = Redis.new(:driver => :hiredis, :host => "localhost", :port => 6379, logger: logger)
when "development"
  REDIS = Redis.new(:driver => :hiredis, :host => "localhost", :port => 6379, logger: logger)
end



## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
