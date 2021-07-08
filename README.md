ZUGFeRD PHP
===========

with additional classes/features!!


----





ZUGFeRD PHP SDK (Factur-X, XRechnung) - Convert PHP Objects to XML and back.

[Look @ Tests for more details](tests)

## Installation
The recommended way of installing this library is using [Composer](http://getcomposer.org/). 

Add this repository to your composer information using the following command

```bash
composer require easybill/zugferd-php
```

## Usage ZUGFeRD v1

Convert XML to PHP Objects:

```php
use Easybill\ZUGFeRD\Reader;

$document = Reader::create()->getDocument('zugferd-file.xml');
echo $document->getHeader()->getId(); // Get invoice No.
```

Convert PHP Objects to XML:

```php
use Easybill\ZUGFeRD\Builder;
use Easybill\ZUGFeRD\Model\Document;
 
$doc = new Document(Document::TYPE_COMFORT);
$doc->getHeader()->setId('RE1337'); // Set invoice No.

$xml = Builder::create()->getXML($doc);
echo $xml; // Zugferd XML.
```

## Usage ZUGFeRD v2.1

Convert XML to PHP Objects:

```php
use Easybill\ZUGFeRD211\Reader;

$xml = file_get_contents('factur-x.xml');
$obj = Reader::create()->transform($xml);
```

Convert PHP Objects to XML:

```php
use Easybill\ZUGFeRD211\Builder;
 
$obj = ...;

$xml = Builder::create()->transform($obj);
echo $xml; // Zugferd XML.
```

## Contributing

Please feel free to send bug reports and pull requests.

## License

Published as open source under the terms of [MIT License](http://opensource.org/licenses/MIT).
