# eKomi APIv3 Client

The library to communicate with eKomi APIv3

## Installation

Install the latest version with

```bash
$ composer require ekomi/api-php
```

## Basic Usage

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\PutOrder;

// init
$api = new Api(APIID,API_KEY);

// generate a new link
$apiCall = new PutOrder();
$apiCall->setOrderId('ekomi-api-test');

$result = $api->exec($apiCall);
var_dump($result);
```

### Requirements

- eKomi APIv3 Client works with PHP 5.3 or above.


# Examples

## getFeedback

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetFeedback;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetFeedback();
$apiCall->setRange('1y');

$result = $api->exec($apiCall);
var_dump($result);
```

## getResearch

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetResearch;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetResearch();
$apiCall->setContent('questions');

$result = $api->exec($apiCall);
var_dump($result);
```

## getProductfeedback

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetProductFeedback;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetProductFeedback();
$apiCall
    ->setProduct('428')
    ->setRange('1y');

$result = $api->exec($apiCall);
var_dump($result);
```

## getProductresearch

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetProductResearch;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetProductResearch();
$apiCall->setContent('questions');

$result = $api->exec($apiCall);
var_dump($result);
```

## getSettings

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetSettings;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetSettings();

$result = $api->exec($apiCall);
var_dump($result);
```

## getSnapshot

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetSnapshot;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetSnapshot();

$result = $api->exec($apiCall);
var_dump($result);
```

## getRated

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetRated;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetRated();
$apiCall->setDays(30);

$result = $api->exec($apiCall);
var_dump($result);
```

## getDialog

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetDialog;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetDialog();

$result = $api->exec($apiCall);
var_dump($result);
```

## getMarketresearch

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetMarketResearch;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetMarketResearch();

$result = $api->exec($apiCall);
var_dump($result);
```

## putOrder

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\PutOrder;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new PutOrder();
$apiCall
    ->setOrderId('ekomi-test')
    ->setProductIds('397,428')
    ->setProductIdsUpdateMethod('replace');

$result = $api->exec($apiCall);
var_dump($result);
```

## putProduct

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\PutProduct;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new PutProduct();
$apiCall
    ->setProductId('ekomi-product')
    ->setProductName('eKomi Product');

$apiCall->getOther()
    ->setImageUrl('https://www.ekomi-us.com/images/us/produkt/siegel/facebook_share_gold_seal.png')
    ->setBrandName('eKomi')
    ->setMpn('mpn')
    ->setUpc('upc')
    ->setEan('ean')
    ->setIsbn('isbn')
    ->setGbase('gbase')

    ->addLinks('http://www.ekomi.de/index.html','canonical');

    //Also You can use it to set canonical link
    //$apiCall->setProductCanonicalLink('http://www.ekomi.de/index.html');

$apiCall->getOther()
    ->addLinks('http://www.ekomi.de/index.html','html');
/**
 * Image urls must be HTTPS
 */
$apiCall->getOther()
    ->addLinks('https://www.ekomi-us.com/images/us/produkt/siegel/facebook_share_gold_seal.png','image')

    ->addCategory('Hey',1)
    ->addCategory('Yes',2)
    ->addCategory('No')

    ->addResearch('ID1')
    ->addResearch('ID2')
    ->addResearch('ID3')
    ->addResearch('ID4')
    ->addResearch('ID_N')

    ->addMetaMatrix('country','Germany')
    ->addMetaMatrix('zip','10969');

$result = $api->exec($apiCall);
var_dump($result);
```

## getVisitorfeedback

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetVisitorfeedback;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetVisitorfeedback();

$result = $api->exec($apiCall);
var_dump($result);
```

## putDialog

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\PutDialog;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new PutDialog();
$apiCall
    ->setOrderId('900162285');
    ->setMessage('Test dialog API');

$result = $api->exec($apiCall);
var_dump($result);
```

## getAverage

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\GetAverage;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new GetAverage();
$apiCall->setDays(3);

$result = $api->exec($apiCall);
var_dump($result);
```

## putClient

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\PutClient;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new PutClient();
$apiCall
    ->setClientId('ekomi-client')
    ->setScreenname('Max W.')
    ->setFirstname('Max')
    ->setLastname('Wright')

    ->addMetaData('children','yes')
    ->addMetaData('language','de');
    
$result = $api->exec($apiCall);
var_dump($result);
```

## assignClientOrder

```php
<?php
use \Ekomi\Api;
use \Ekomi\Request\AssignClientOrder;

// init
$api = new Api(APIID,API_KEY);

$apiCall = new AssignClientOrder();

$apiCall
    ->setOrderId("ekomi-test")
    ->setClientId("ekomi-client");
    
$result = $api->exec($apiCall);
var_dump($result);
```