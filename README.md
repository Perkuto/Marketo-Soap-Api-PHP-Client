Extended Marketo SOAP API Client for PHP 
===================================================

### Motivation

* Add missing SOAP API endpoints

### Requirements

 * PHP >= 5.3.0
 * PHP Extensions : SOAP and cURL for SSL support

### Installation

```json
...
"require": {
        ...
        "perkuto/marketo-soap-api-php-client": "1.0*@master"
    }
...
```

### Usage

```php
require_once 'route/to/MarketoSoapApiClient.php';

use au\com\hooshmarketing\marketoconnector\modules\marketosoapapiclient\MarketoSoapApiClient;

// replace with your Marketo soap endpoint (without ?WSDL at the end)
$soapEndpoint = 'https://<YOUR-MUNCHKIN-ID>.mktoapi.com/soap/mktows/2_2';

try {
    $marketoSoapApiClient = new MarketoSoapApiClient(
        '<YOUR-MARKETO-API-USER-ID>',
        '<YOUR-MARKETO-SECRET-KEY>',
        new SoapClient(
            $soapEndpoint."?WSDL", 
            MarketoSoapApiClient::buildOptionsArray($soapEndpoint)
        )
    );
} catch (SoapFault $ex){
    // Error connecting to Marketo SOAP Endpoint
    // ...
}
```

```php
$leadCookie = ''; // fill in with some lead cookie value you want to test

var_export(
    $marketoSoapApiClient->getLeadBy(
        'COOKIE',
        $leadCookie
    )
);
```

===================================================

### Fork of Marketo SOAP API PHP (micro-) Client by elcodedocle

 * Copyright (C) 2014 Gael Abadi
 * License: [MIT Expat][1]
 * Version: 0.2.0-beta

### Acknoweldgements

[Ben Ubois](https://github.com/benubois), the developer behind 
[Marketo](https://github.com/flickerbox/marketo), "A PHP client for the Marketo SOAP API"

### License

https://raw.githubusercontent.com/elcodedocle/marketo-soap-api-php-client/master/LICENSE
