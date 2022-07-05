# Laravel Debugbar Extension

This package allows you to enable the Debugbar on deman, despite being disabled by configuration.

```ini
DEBUGBAR_ENABLED=false
```

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

**Middleware**

```php
public function handle($request, Closure $next){
    if(/* your validation*/){
        \Debugbar::enable();
    }
    return $next($request);
}
```

