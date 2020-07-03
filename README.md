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
https://stackoverflow.com/questions/43341820/laravel-echo-allow-guests-to-connect-to-presence-channel
