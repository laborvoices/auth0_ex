# Auth0Ex

[![Hex version](https://img.shields.io/hexpm/v/auth0_ex.svg "Hex version")](https://hex.pm/packages/auth0_ex) ![Hex downloads](https://img.shields.io/hexpm/dt/auth0_ex.svg "Hex downloads") [![Build Status](https://travis-ci.org/techgaun/auth0_ex.svg?branch=master)](https://travis-ci.org/techgaun/auth0_ex)

> An elixir client library for Auth0

## Installation

You can install the stable version from hex:

```elixir
def deps do
[{:auth0_ex, "~> 0.1"}]
end
```

You can use github repo as your package source to use the latest source code but beware it might have breaking and unstable code:

```elixir
def deps do
  [{:auth0_ex, github: "techgaun/auth0_ex"}]
end
```

Ensure `auth0_ex` is started before your application:

```elixir
def application do
  [applications: [:auth0_ex]]
end
```

## Configuration

Add a configuration block like below:

- First option is to use management api client.

You can create non-interactive client for management api as described [HERE](https://auth0.com/docs/api/management/v2/tokens).
Once you do that, you should be able to grab client ID and client secret from the setting page for use with Auth0Ex.
This is a recommended setup as Auth0Ex can recreate new `access_token` when the current one expires.

```elixir
config :auth0_ex,
  domain: System.get_env("AUTH0_DOMAIN"),
  mgmt_client_id: System.get_env("AUTH0_MGMT_CLIENT_ID"),
  mgmt_client_secret: System.get_env("AUTH0_MGMT_CLIENT_SECRET"),
  http_opts: []
```

- Second option is to use pre-created token with access to management API.

```elixir
config :auth0_ex,
  domain: System.get_env("AUTH0_DOMAIN"),
  mgmt_token: System.get_env("AUTH0_MGMT_TOKEN"),
  http_opts: []
```

_Note: if you use pre-created management token, it will always be used for your requests_

Export appropriate environment variable and you should be all set.

Please refer to the [documentation](https://hexdocs.pm/auth0_ex/) for more details.

### Authentication API

In addition to the management API resources, there is also a support for most used authentication APIs.
Authentication API will use the same `domain` config you specify in the config above. If you wish to use `Auth0Ex`
for authentication APIs only, all you need to specify is `domain` in config.

## Author

- [techgaun](https://github.com/techgaun)
