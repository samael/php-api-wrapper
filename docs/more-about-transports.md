# The Transport

The Transport is an implementation of `TransportInterface`, it manages the API Autentication, 
returns deserialized data, and manage HTTP errors with `ApiException` and childs (see `src/Exceptions`).

## Use an existing transport

Several implementations already exist ([see the folder](../src/Transports)) :

- [`Cristal\ApiWrapper\Transports\Transport`](../src/Transports/Transport.php) Generic JSON API without authentication
- [`Cristal\ApiWrapper\Transports\Bearer`](../src/Transports/Bearer.php) Extends of `Transport` supports bearers tokens
- [`Cristal\ApiWrapper\Transports\Basic`](../src/Transports/Basic.php) Extends of `Transport` supports basic auth
- `Cristal\ApiWrapper\Transports\OAuth2` Extends of `Transport` supports OAuth2 ([see doc](transports/oauth2.md))

## Create a custom transport

You are likely to have to manage complex authentication, in this case your can create you own implementation of TransportInterface.

See more about the [TransportInterface here](../src/Transports/TransportInterface.php).

## Example of usage :

```php
<?php

use Cristal\ApiWrapper\Transports\Basic;
use Curl\Curl;

$transport = new Basic('username', 'password', 'http://api.example.com/v1/', new Curl);
$users = $transport->request('/users');
```

## Next

Now that you've got transport, you're ready to implement your Wrapper.

[Learn more about Wrapper](more-about-wrapper.md).
