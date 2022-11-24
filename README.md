# Laravel Debugbar Extension

This package allows you to enable the Debugbar on deman, despite being disabled by configuration.

## Installation

```bash
composer require jaguarsoft/laravel-debugbar
```

## Configuration

**config/app.php**

```php
'providers' => [   
    /** **/ 
    // Barryvdh\Debugbar\ServiceProvider::class,
    JaguarSoft\LaravelDebugbar\Provider\DebugbarServiceProvider::class,
],
'aliases' => [
    /** **/
    'Debugbar' => Barryvdh\Debugbar\Facade::class,
],
```

## Use

**To load Enabled for All**
```ini
DEBUGBAR_ENABLED=true
```
**To load Disable for All, enabled after in a Middleware**
```ini
DEBUGBAR_ENABLED=false
```
**To load Enabled when** `APP_DEBUG=true`
```ini
DEBUGBAR_ENABLED=null
```

### Middleware

```php
public function handle($request, Closure $next){
    if(/* your validation*/){
        \Debugbar::enable();
    }
    return $next($request);
}
```

**Example Middleware:** [https://gist.github.com/laurenceHR/911050c675eb5a1d28b761b61b3b25a0
](https://gist.github.com/laurenceHR/911050c675eb5a1d28b761b61b3b25a0)

Used and Tested in Laravel 5.2, 5.3, 5.4
Is not necessary in Laravel 5.5 because with "barryvdh/laravel-debugbar" version "~3.4.2" has this feature included.
