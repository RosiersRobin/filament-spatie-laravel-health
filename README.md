# Filament Spatie Laravel Health

[![PHP Version Require](http://poser.pugx.org/shuvroroy/filament-spatie-laravel-health/require/php)](https://packagist.org/packages/shuvroroy/filament-spatie-laravel-health)
[![GitHub Tests Action Status](https://img.shields.io/github/actions/workflow/status/shuvroroy/filament-spatie-laravel-health/run-tests.yml?branch=main&label=tests)](https://github.com/shuvroroy/filament-spatie-laravel-health/actions?query=workflow%3Arun-tests+branch%3Amain)
[![Latest Stable Version](http://poser.pugx.org/shuvroroy/filament-spatie-laravel-health/v)](https://packagist.org/packages/shuvroroy/filament-spatie-laravel-health)
[![Total Downloads](http://poser.pugx.org/shuvroroy/filament-spatie-laravel-health/downloads)](https://packagist.org/packages/shuvroroy/filament-spatie-laravel-health)
[![License](http://poser.pugx.org/shuvroroy/filament-spatie-laravel-health/license)](https://packagist.org/packages/shuvroroy/filament-spatie-laravel-health)

This package provides a Filament page that you can monitor the health of your application by registering checks using the [spatie/laravel-health](https://spatie.be/docs/laravel-health/v1/introduction) package.

![Health Check Results - Filament Demo](https://user-images.githubusercontent.com/21066418/147746698-8a21ab58-1771-4525-9595-0bbcedc6a325.png)

## Support For This Project

<a href="https://www.buymeacoffee.com/shuvroroy" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

## Installation

You can install the package via composer:

```bash
composer require shuvroroy/filament-spatie-laravel-health
```

This package can store health check results [in various ways](https://spatie.be/docs/laravel-health/v1/storing-results/general). When using the EloquentHealthResultStore the check results will be stored in the database. To create the health_check_result_history_items table, you must create and run the migration.

```bash
php artisan vendor:publish --tag="health-migrations"
php artisan migrate
```

You can publish the config file with:

```bash
php artisan vendor:publish --tag="filament-spatie-health-config"
```

This is the contents of the published config file:

```php
return [

    /*
    |--------------------------------------------------------------------------
    | Pages
    |--------------------------------------------------------------------------
    |
    | This is the configuration for the general appearance of the page
    | in admin panel.
    |
    */

    'pages' => [
        'health' => \ShuvroRoy\FilamentSpatieLaravelHealth\Pages\HealthCheckResults::class
    ],

];
```

## Usage

This package will automatically register the `HealthCheckResults`. You'll be able to see it when you visit your Filament admin panel.

## Defining Resources to health check

 Register Health::checks on app/Providers/AppServiceProvider.php -> `boot` method

 ```php
<?php

namespace App\Providers;

use Spatie\Health\Facades\Health;
use Spatie\Health\Checks\Checks\OptimizedAppCheck;
use Spatie\Health\Checks\Checks\DebugModeCheck;
use Spatie\Health\Checks\Checks\EnvironmentCheck;

class AppServiceProvider extends ServiceProvider
{
     public function boot()
     {
         Health::checks([
             OptimizedAppCheck::new(),
             DebugModeCheck::new(),
             EnvironmentCheck::new(),
         ]);
     }
 }
 ```

 Read the full documentation on [Spatie Laravel Health](https://spatie.be/docs/laravel-health/v1/available-checks/overview)

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Shuvro Roy](https://github.com/shuvroroy)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
