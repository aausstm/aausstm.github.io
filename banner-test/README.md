# README

## Description
Proof of concept that displays an add-to-homescreen banner on android mobile
and uses a service-worker that shows an offline-site if disconnected to network.

### add-to-homescreen-banner

will only work when a number of criteria have been met:

- The app uses a service worker
- The site is using HTTPS
- The app has a manifest declared
- The manifest has a short_name, 144 pixel icon and a type of 'image/png'


### service worker

The offline service worker adds an offline.html to the cache and fetches
get requests of type text/html.
If a request fails it displays the offline.html page.

Add the following script somewhere in you index.html to register the service worker:

`
<script>
    navigator.serviceWorker.register('sw.js', { scope: './' })
      .then(function(registration) {
        // Registration was successful
        console.log('ServiceWorker registration successful with scope: ', registration.scope);
      }).catch(function(err) {
        // registration failed :(
        console.log('ServiceWorker registration failed: ', err);
      });
</script>
`
