# Cardinal-Project

#### One place for technical information, issues, discussion, and suggestions for all Cardinal apps.

If you run into a bug or problem of any kind with **any** Cardinal app, this is the right place to let the Cardinal developer know. Please create a new [issue](https://github.com/somebeaver/Cardinal-Project/issues/new) describing the problem if an issue for it doesn't already exist.

For general suggestions/feedback, this GitHub repo and [Reddit](https://old.reddit.com/r/cardinalapps) are good places to start a discussion.

## Apps

The Cardinal project is comprised of an ecosystem of apps. Items in bold have been released, other items are either in development or planned for the future.

Name | Features | Platforms | Releases
------------ | ------------ | ------------- | ------------
**Cardinal Server** | [See web page](https://cardinalapps.xyz/en/cardinal-server) | **macOS**, **Windows**, Linux, Docker | [Downloads](https://github.com/somebeaver/Cardinal-Server)
**Cardinal Music** | [See web page](https://cardinalapps.xyz/en/cardinal-music) | **macOS**, **Windows**, Linux, mobile (PWA & native) | [Downloads](https://github.com/somebeaver/Cardinal-Music)
Cardinal Photos | TBA | macOS, Windows, Linux, mobile (PWA & native) | -
Cardinal TV & Movies | TBA | macOS, Windows, Linux, mobile (PWA & native) | -
Cardinal Books | TBA | macOS, Windows, Linux, mobile (PWA & native) | -

## Development Philosophy

Cardinal apps embrace a few simple concepts.

- **Privacy above all**
  - Nothing in the apps is tracked. Nothing is sent to a server. There's no bundled analytics software. No email address or account required. This is modern old school software.
- **As platformless as possible**
  - Web technology is platformless. It is flexible and accessible. It is modern, fast, and reliable. Cardinal apps are designed to run platformless first, i.e., no native app, instead just running in some web browser. By designing for the web first, mode code covers more platforms.
  - Native apps are used to wrap the web apps, to provide them with system functionality that web apps don't normally have. Thing like file system access, and access to the media keys on a keyboard, but also less obvious things like multiprocessing.
- **Offline first**
  - Building on the modern old school approach, Cardinal apps are all designed to work without ever having internet access. Every app can run on 100% local metadata, and there will never be any sort of forced authentication.

## Tech Stack

All apps are written in vanilla JavaScript. The JS that runs in Node.js uses CJS packages, and the JS that runs in a browser uses ES6 packages.

Most of the libraries that Cardinal depends on were written specifically for Cardinal and have been open sourced. When possible, Cardinal prefers to rely on first party solutions.
