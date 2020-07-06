# FAQ

**Q1:** Access to XMLHttpRequest at 'https://domain-a.local/user' from origin 'https://domain-b.local' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
**A:** Add belows command to virtual host (apache2) of **domain-a.local**, restart apache2 server and done!
```
<Directory "/var/www/xyz/public">
       ...
		Header set Access-Control-Allow-Origin "*"
	</Directory>
```
**Q2:** Access to XMLHttpRequest at 'https://domain-a.local/user' from origin 'https://domain-b.local' has been blocked by CORS policy: Request header field x-csrf-token is not allowed by Access-Control-Allow-Headers in preflight response.
**A:** Add belows command to virtual host (apache2) of **domain-a.local**, restart apache2 server and done!
```
<Directory "/var/www/xyz/public">
       ...
		Header set Access-Control-Allow-Headers "Content-Type,Authorization, X-Requested-With,X-CSRF-Token"
	</Directory>
```
**Q3:** How to force Laravel Project to use HTTPS for all routes?
**A:** Force Https in Laravel 7.x (2020)
"2020 Update? Url::forceScheme was acting funky for me, but this worked liked a dime."

https code snippet.

resolve(\Illuminate\Routing\UrlGenerator::class)->forceScheme('https');

Add that snippet within any Service Provider Boot Method
1: Open app/providers/RouteServiceProvider.php.
2: Then add the https code snippet to the boot method.
```
    /**
     * Define your route model bindings, pattern filters, etc.
     *
     * @return void
     */
    public function boot()
    {
        resolve(\Illuminate\Routing\UrlGenerator::class)->forceScheme('https');

        parent::boot();
    }
```
3: Lastly run php artisan route:clear && composer dumpautoload to clear Laravel's cached routes and cached Service Providers.






References:
https://stackoverflow.com/questions/43341820/laravel-echo-allow-guests-to-connect-to-presence-channel
https://stackoverflow.com/questions/35827062/how-to-force-laravel-project-to-use-https-for-all-routes
