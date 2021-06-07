<p align="center">
  <a href="https://cardinalapps.xyz"><img src="https://cardinalapps.xyz/logotype-dark.svg" width="460" /></a>
</p>

<h3 align="center">Technical information and feedback for all Cardinal apps.</h3>

[Cardinal](https://cardinalapps.xyz) is an ecosystem of apps for your digital media. Use the Cardinal Server to index your music, photos, TV & movies and books, and use the various apps to browse your libraries and play your media.

## Apps

Items in bold have been released, other items are either in development or planned for the future.

Name | Features | Platforms | Releases
------------ | ------------ | ------------- | ------------
**Cardinal Server** | [See web page](https://cardinalapps.xyz/en/cardinal-server) | **macOS**, **Windows**, Linux, Docker | [Downloads](https://github.com/somebeaver/Cardinal-Server)
**Cardinal Music** | [See web page](https://cardinalapps.xyz/en/cardinal-music) | **macOS**, **Windows**, Linux, mobile (PWA & native) | [Downloads](https://github.com/somebeaver/Cardinal-Music)
Cardinal Photos | TBA | macOS, Windows, Linux, mobile (PWA & native) | -
Cardinal TV & Movies | TBA | macOS, Windows, Linux, mobile (PWA & native) | -
Cardinal Books | TBA | macOS, Windows, Linux, mobile (PWA & native) | -

## Current State

![Generic badge](https://img.shields.io/badge/Status-In&nbsp;Development-brightgreen.svg)
![Generic badge](https://img.shields.io/badge/Release-Early&nbsp;Access-informational.svg)

The project is under active development and new releases continue. All releases before v1.0.0 are considered early access. They work well, but lack some of the features necessary to be considered production ready. Please see [this section](#early-access-considerations) about early access before making Cardinal your main media platform.

## Tech Stack

Everything is written in vanilla JavaScript. The JS that runs in Node.js uses CJS packages, and the JS that runs in a browser uses ES6 packages.

**Most of the libraries that Cardinal depends on were written specifically for Cardinal and have been open sourced**. When possible, Cardinal prefers to rely on first party solutions. These are the main packages that any Cardinal app uses:

### First Party Libraries
- [Lowrider.js](https://github.com/somebeaver/Lowrider.js) - Enhanced web components.
- [cardinal-indexing-service](https://github.com/somebeaver/cardinal-indexing-service) - The service that the server uses to index files.
- [double-u](https://github.com/somebeaver/double-u) - DOM manipulation.
- [Bridge.js](https://github.com/somebeaver/Bridge.js) - Client to server HTTP, WebSocket, and IPC communication.
- [sqleary.js](https://github.com/somebeaver/sqleary.js) - SQL query builder.
- [router.js](https://github.com/somebeaver/router.js) - UI routing.
- [html.js](https://github.com/somebeaver/html.js) - HTML file templating.
- [Boogietime.js](https://github.com/somebeaver/Boogietime.js) - Application level audio playback; wraps howler.js.
- +7 other first party libraries to be open sourced

### Third Party Libraries
- [Electron](https://www.electronjs.org/) - Runs Cardinal apps on the desktop and provides them with system functionality and multiprocessing.
- [sqlite3](https://www.npmjs.com/package/sqlite3) - Database driver for server and client apps on the desktop and Docker.
- [Fastify](https://www.npmjs.com/package/fastify) - HTTP server.
- [ws.js](https://www.npmjs.com/package/ws) - WebSocket server. Clients use the native `WebSocket` browser API.
- [Swiper](https://swiperjs.com/) - HTML carousels on deskop and mobile in all apps.
- [howler.js](https://howlerjs.com/) - HTML5 audio playback in Cardinal Music; gets wrapped by Boogietime.js.

For a complete list of dependencies, click "Open Source" in the menu of any Cardinal app.

### Database Layer

The database is powered by sqlite3. Each Electron app gets its own database, although most data lives in the server database. The CRUD functions and the API use plain SQL. For working with queries, [sqleary.js](https://github.com/somebeaver/sqleary.js) was purpose built.

The apps also use the [Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API).

### Presentation Layer

UI's are [single-page applications](https://en.wikipedia.org/wiki/Single-page_application) powered by [Lowrider.js](https://github.com/somebeaver/Lowrider.js) web components. Components are typically designed for a single purpose in single app, but they can also be shared between apps (e.g., the settings panel is shared between all apps).

View routing is handled by [router.js](https://github.com/somebeaver/router.js), which handles the state of the UI and provides browsing functionality. Templates are handled by [html.js](https://github.com/somebeaver/html.js), which implements rudementary templating features like `{{mustache-tags}}`, and nested templates.

### Networking Layer

The server app uses Fastify for the HTTP server, and ws.js for WebSockets. Media is streamed over the network from the server to the clients, however clients can also play media locally.

The server provides a RESTful API for consuming media data.

## Roadmap

**Short term:**
- Music app PWA.
- More music features and improvements.
- More server features and improvements.

**Medium term:**
- Photos app release.
- `server -> internet -> client` data streaming to remove the LAN-only constraint.

## Development Philosophy

Cardinal apps embrace a few simple concepts.

- **As platformless as possible**
  - Web technology is platformless. It is flexible and accessible. It is modern, fast, reliable, and without a corporation gatekeeping an app store. Cardinal apps are designed to run platformless first, i.e., no native app, instead just running in some web browser. By designing for the web first, more code covers more platforms.
  - Native apps are used to wrap the web apps, to provide them with system functionality that web apps don't normally have. File system access, multiprocessing, better databases, and much more.
- **Privacy above all**
  - Nothing in the apps is tracked. Nothing is sent to a server. There's no bundled analytics software. No email address or account required. The apps should feel like modern old school software.
- **Offline first**
  - Building on the modern old school approach, Cardinal apps are all designed around never having internet access. The UI shouldn't feel lacking just because the user doesn't want to download hundreds of artist images or album covers.

## Early Access Considerations

Cardinal apps are early access software, and as such, are subject to breaking changes. There is an effort to ensure that changes impact users as little as possible, however, expect to have to reset your server database before the stable v1.0.0 release. Fortunately, the process to do so is literally just 1 button.

Additionally, apps are Local Area Network only for now. Client apps must be on the same LAN as the server app. Internet playback is on the (roadmap)[#roadmap], and may be fast-tracked depending on user demand.

## Contributing

The best way to contribute code will be to write a [plugin](https://cardinalapps.xyz/plugins). The plugin system is currently in development.

## Licenses

All of the [first party libraries](#first-party-libraries) that were created for Cardinal are licensed under the [Mozilla Public License 2.0](https://choosealicense.com/licenses/mpl-2.0/). The rest of the Cardinal project is distributed as freeware.
