<p align="center">
  <a href="https://cardinalapps.xyz"><img src="https://cardinalapps.xyz/logotype-dark.svg" width="460" /></a>
</p>

<h3 align="center">Technical information and feedback for all Cardinal apps</h3>

[![Cardinal Discord Invite](https://img.shields.io/discord/852722597136433172?color=%237289DA&label=chat&logo=discord&logoColor=white)](https://discord.com/invite/WWXngggPp4)
[![Generic badge](https://img.shields.io/badge/Status-In&nbsp;Development-brightgreen.svg)](#)
[![Generic badge](https://img.shields.io/badge/Release-Early&nbsp;Access-informational.svg)](#)

[Cardinal](https://cardinalapps.xyz) is an ecosystem of apps for your digital media. Use Cardinal Server to index your music, photos, books, and TV & movies, and use the various client apps to browse your libraries and consume your media.

## Apps

**Items in bold have been released**, *items in italics are either in development or planned for the future*.

Name | Features | Platforms | Releases
------------ | ------------ | ------------- | ------------
**Cardinal Server** | [See web page](https://cardinalapps.xyz/en/cardinal-server) | **macOS**, **Windows**, *Linux*, *Docker* | [Downloads](https://github.com/somebeaver/Cardinal-Server)
**Cardinal Music** | [See web page](https://cardinalapps.xyz/en/cardinal-music) | **macOS**, **Windows**, **Linux**, **mobile** (**web**, *native*) | [Downloads](https://github.com/somebeaver/Cardinal-Music)
*Cardinal Photos* | TBA | *macOS*, *Windows*, *Linux*, *mobile* (*web*, *native*) | -
*Cardinal TV & Movies* | TBA | *macOS*, *Windows*, *Linux*, *mobile* (*web*, *native*) | -
*Cardinal Books* | TBA | *macOS*, *Windows*, *Linux*, *mobile* (*web*, *native*) | -

## Current State

The project is in part time development and new releases continue. All releases before v1.0.0 are considered early access. Please see [this section](#early-access-considerations) about early access before making Cardinal your main media platform.

## Tech Stack

Everything is written in vanilla JavaScript.

**Many of the libraries that Cardinal depends on were purpose built for Cardinal and have been open sourced.** When possible, Cardinal prefers to rely on first party solutions. Below is a non-exhaustive list of libraries that the apps use:

### First Party Libraries
- [Lowrider.js](https://github.com/somebeaver/Lowrider.js) - Enhanced web components.
- [cardinal-indexing-service](https://github.com/somebeaver/cardinal-indexing-service) - The service that the server uses to index files.
- [double-u](https://github.com/somebeaver/double-u) - DOM manipulation.
- [Bridge.js](https://github.com/somebeaver/Bridge.js) - Client to server HTTP, WebSocket, and IPC communication.
- [sqleary.js](https://github.com/somebeaver/sqleary.js) - SQL query builder.
- [router.js](https://github.com/somebeaver/router.js) - UI routing.
- [html.js](https://github.com/somebeaver/html.js) - HTML file templating.
- [Boogietime.js](https://github.com/somebeaver/Boogietime.js) - Application level audio playback; wraps howler.js.
- ...and more to be open sourced

### Third Party Libraries
- [Electron](https://www.electronjs.org/) - Runs Cardinal apps on the desktop and provides them with OS integrations and multiprocessing.
- [sqlite3](https://www.npmjs.com/package/sqlite3) - Database driver for server and client apps on the desktop and Docker.
- [Fastify](https://www.npmjs.com/package/fastify) - HTTP server.
- [ws.js](https://www.npmjs.com/package/ws) - WebSocket server. Clients use the native `WebSocket` browser API.
- [Swiper](https://swiperjs.com/) - HTML carousels on deskop and mobile in all apps.
- [howler.js](https://howlerjs.com/) - Audio playback in Cardinal Music; gets wrapped by Boogietime.js.

For a complete list of dependencies that a Cardinal app uses, click "Open Source" in its menu.

### Database Layer

The database is powered by SQLite. Each Electron app gets its own database, although the majority of data lives in the server database. CRUD functions and the API use plain SQL. For advanced queries, [sqleary.js](https://github.com/somebeaver/sqleary.js) was purpose built.

The apps also use the [Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API) in the Electron renderers for simple key-value storage.

### Presentation Layer

All app UIs are a single-page applications powered by [router.js](https://github.com/somebeaver/Router.js). UI components are [Lowrider.js](https://github.com/somebeaver/Lowrider.js) web components. Components are typically designed for a single purpose in single app, but they can also be shared between apps (e.g., the settings panel is shared between all apps).

Templates are handled by [html.js](https://github.com/somebeaver/html.js), which provides templating features like `{{mustache-tags}}` and nested templates.

Working with the DOM is done with [double-u](https://github.com/somebeaver/double-u), a jQuery inspired library that also provides general purpose frontend helpers.

The single-page applications are responsive web apps designed to run in web browsers on the desktop, tablet, and smartphone, and are also ready to be progressively enhanced by Electron on the desktop and native apps on mobile.

### Networking Layer

The server app uses Fastify for the HTTP server, and ws.js for WebSockets. Media is streamed over the network from the server to the clients, but clients can also play media locally and report their playback status to the server.

The server provides a RESTful HTTP API for consuming media data.

## Roadmap

**Ongoing**
- New features and improvements for released apps.

**Short term:**
- Server Docker CLI release.
- Linux desktop builds for Server and Music.

**Medium term:**
- Server full size UI.
- Photos app early access.
- `server -> internet -> client` data streaming to remove the LAN-only constraint.

## Development Philosophy

Cardinal apps embrace a few simple concepts.

- **To be as platformless as possible**
  - Web technology is platformless, flexible, accessible, and without a corporation gatekeeping an app store. Cardinal apps embrace the web stack, and by designing for the web first, more code covers more platforms.
  - Native apps can be used to wrap and progressively enhance the web apps, to provide them with system functionality and features like file system access, multiprocessing, better databases, and more.
- **Freedom from advertising**
  - All apps are free of tracking, marketing, and ads. No "Updgrade Now" buttons. No paywalled features. No phoning home. No crypto mining. No bundled analytics software. No email address or account required. And of course, no auth servers.
- **Offline first**
  - The apps are designed around never having internet access. The UI's should maximize the use of local metadata.

## Early Access Considerations

Cardinal apps are early access software, and as such, are subject to breaking changes. Expect to have to reset your server database before the stable v1.0.0 release.

Additionally, apps are restricted to the local area network. Client apps must be on the same network as the server app. Internet playback is on the [roadmap](#roadmap), and may be fast-tracked depending on user demand.

## Contributing

The best way to contribute code will be to write a [plugin](https://cardinalapps.xyz/plugins). The plugin system is currently in development, check back soon.

## Licenses

All of the [first party libraries](#first-party-libraries) that were created for Cardinal are open source and licensed under the [Mozilla Public License 2.0](https://choosealicense.com/licenses/mpl-2.0/). The rest of the Cardinal project is distributed as freeware.
