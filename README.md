# Ringcaptcha API

Set up your Ringcaptcha keys (eg in config/initializers/ringcaptcha.rb): 

    Ringcaptcha.app_key = '...'
    Ringcaptcha.api_key = '...'
    Ringcaptcha.secret_key = '...'

## Normalize Numbers & Info:

   response = Ringcaptcha.normalize('353 083 148 0349')

   response #=> <Ringcaptcha::Response status="SUCCESS", phone="+353831480348", country="IE", area=nil, block=nil, subscriber=nil, type="MOBILE", carrier="Vodafone">
   response.success?   #=> true
   response.error?     #=> false
   response.status     #=> "SUCCESS"
   response.phone      #=> "+353831480349"
   response.country    #=> "IE"
   response.area       #=> nil
   response.block      #=> nil
   response.subscriber #=> nil
   response.type       #=> "MOBILE"
   response.carrier    #=> "Vodafone"

## Installation

Add this line to your application's Gemfile:

    gem 'ringcaptcha'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install ringcaptcha

## Usage

TODO: Write usage instructions here

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
