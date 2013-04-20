# Rate Limiter for Prism Realtime Server

This very basic rate limiter prevents malicious users from flooding the server with multiple requests per second - something that's easy to do on the client if you use a while loop in the JS console.

For now this module mostly serves as an example of how to create Prism request middleware.


## Example Usage

```js
// in your server config
server.use(require('prism-rate-limiter')({maxRequestsPerSecond: 12})); // default = 8

```

## How it works

The middleware counts each incoming request for every `socketId`. Normally requests are just passed through, however if the client has exceeded its allocation, we send a warning (visible in the browser's console) and drop the message.

The warning will only be sent once. All subsequent requests will be silently dropped.

The request counter is reset every second.


## TODO

* Add an option to drop all future traffic from an offending client
* Add ability to whitelist hosts


## Tests

    mocha


## License

MIT