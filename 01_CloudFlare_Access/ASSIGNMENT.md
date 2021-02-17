# CloudFlare Access

Create a M2 module that will authorize CloudFlare Access requests. The documentation for CloudFlare Access request validation is [here](https://developers.cloudflare.com/cloudflare-one/identity/users/validating-json#python-example).

1. Intercept all requests to Magento frontend controllers. You can use Plugins or Observers.
2. If the request doesn't have a `CF_Authorization` cookie, then return a 403 with the message
```
missing required cf authorization token
```
3. If the cookie is present, then allow the request to pass through.
4. A store configuration setting should determine if the module is Enabled / Disabled. Default should be `false`.

Relevant documentation:
* [Routing](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html)
* [Plugins](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/plugins.html)
* [Observers](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/events-and-observers.html) and [M2 Event Cheatsheet](https://www.mageplaza.com/magento-2-module-development/magento-2-events.html)