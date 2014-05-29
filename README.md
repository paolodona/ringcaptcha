# Ringcaptcha API

Set up your Ringcaptcha keys (eg in config/initializers/ringcaptcha.rb): 

    Ringcaptcha.app_key = '...'
    Ringcaptcha.api_key = '...'
    Ringcaptcha.secret_key = '...'

## Installation

Add this line to your application's Gemfile:

    gem 'ringcaptcha', :git => 'https://github.com/paolodona/ringcaptcha.git'

And then execute:

    $ bundle

## Usage: Normalize Numbers:

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

## Usage: Verifying Phone Numbers:

    # Step 1 - Get a captcha token

    locale = "de"
    response = Ringcaptcha.captcha(locale)
  
    response.token # => "31b0332942cc4e274118098f95cba64f8eb413fa"

    # Step 2 - Send the PIN code
 
    token = response.token
    phone = "+353831480349"
    service = "sms"
    Ringcaptcha.code(token, phone, service)

    # Step 3 - Verify the PIN code

    code = "1234"
    response = Ringcaptcha.verify(token, code)

    response #=> #<Ringcaptcha::Response status="SUCCESS",id="2381555c031619e61b3f81af30445b27a87ae97a", phone="+353831480349", geolocation=1, phone_type="MOBILE", carrier="Vodafone", threat_level="LOW">

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
