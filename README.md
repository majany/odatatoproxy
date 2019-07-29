# OdataToProxy middleware extension for ui5 tooling express server

Allows you to forward the odata requests of your ui5 app to the
in ui5 tooling integrated proxy running at localhost:8080/proxy

The proxy can already be configured to serve an arbitrary host.

In combination this middleware and the proxy allow you to forward your odata request to a host of your liking. This makes it easy to run your ui5 app against any real backend instance serving your odata service. It circumvents CORS issues

## Usage

 * add this package to your npm dependencies of your ui5 app
 * add the middleware  usage definition to the ui5.yaml of your app. Set ``beforeMiddleWare`` to ``connectUI5Proxy`` middleware. 
```javascript
server:
  customMiddleware:
    - name: odatatoproxy
      beforeMiddleware: connectUi5Proxy
```
 * Now set the environment variable ``REMOTE_LOCATION`` to the host of your service.
 * The middleware automatically determines the path to your odata service from the manifest.json file.
 * e.g. you want to use the odata service at https://services.odata.org/V2/OData/OData.svc/, then you need to set ``REMOTE_LOCATION `` to https://services.odata.org and your manifest.json should contain ``/V2/OData/OData.svc/`` as mainService uri.
