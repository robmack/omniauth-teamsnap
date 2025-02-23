# OmniAuth TeamSnap

[![Gem Version](https://badge.fury.io/rb/omniauth-teamsnap.svg)](https://badge.fury.io/rb/omniauth-teamsnap)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This is the official OmniAuth strategy for authenticating to TeamSnap. To
use it, you'll need to sign up for an OAuth2 Application Id and Secret
on [Cogsworth](https://auth.teamsnap.com).

## Basic Usage

    use OmniAuth::Builder do
      provider :teamsnap, ENV['TEAMSNAP_KEY'], ENV['TEAMSNAP_SECRET']
      # provider :teamsnap, Rails.application.credentials.teamsnap_key, Rails.application.credentials.teamsnap_secret # if using Rails' credentials file
    end

## Scopes

TeamSnap API v3 lets you set scopes to provide granular access to different types of data:

    use OmniAuth::Builder do
      provider :teamsnap, ENV['TEAMSNAP_KEY'], ENV['TEAMSNAP_SECRET'], scope: "read write"
    end

## Authentication Hash
An example auth hash available in `request.env['omniauth.auth']`:

```
{
  :provider => "teamsnap",
  :uid => "123456",
  :info => {
    :email => "player@example.com",
    :first_name => "John",
    :last_name => "Player",
  },
  :credentials => {
    :token => "a1b2c3d4...", # The OAuth 2.0 access token
  },
  :extra = {}
}
```

## Testing

```
docker build . -t omniauth-teamsnap:test -f Test.dockerfile
docker run -t omniauth-teamsnap:test
docker image rm omniauth-teamsnap:test --force
```
