# vs-remote-debugger (PHP SDK)

[![Latest Stable Version](https://poser.pugx.org/mkloubert/vs-remote-debugger/version)](https://packagist.org/packages/mkloubert/vs-remote-debugger)

Server-side PHP library for interacting with [vs-remote-debugger](https://github.com/mkloubert/vs-remote-debugger) Visual Studio Code extension, e.g.

[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=GFV9X2A64ZK3Y)

## License

[MIT license](https://github.com/mkloubert/vs-remote-debugger/blob/master/LICENSE)

## Install

Install the [RemoteDebugger.php](https://github.com/mkloubert/php-remote-debugger/blob/master/src/MJK/Diagnostics/RemoteDebugger.php) in your application.

A common way is to use [Composer](https://getcomposer.org/) to install anything via [Packagist.org](https://packagist.org/packages/mkloubert/vs-remote-debugger):

```bash
composer require mkloubert/vs-remote-debugger
```

## Usage

If you look at the [example code](https://github.com/mkloubert/php-remote-debugger/blob/master/tests/test1.inc.php) you can see how the class can be used:

```php
$debugger = new \MJK\Diagnostics\RemoteDebugger();
$debugger->addHost("my.remote.host.or.ip", 23979);

// compress JSON data with GZIP
// 
// activate the "gzip" plugin in your
// launch.json file in VS Code!
$debugger->JsonTransformer = function($json) {
    return @\gzencode($json);
};

// send the information you want to debug
$debugger->dbg([
    'a' => date('Y-m-d H:i:s'),
    'b' => 1,
    'c' => 2.34,
    'd' => 'Marcel K! Marcel K! Marcel K!',
    'e' => false,
    'f' => null,
    'g' => true,
]);
```
