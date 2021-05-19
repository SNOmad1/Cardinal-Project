# Cardinal-Project

#### One place for information, issues, discussion, and suggestions for all Cardinal apps.

If you run into a bug or problem of any kind with **any** Cardinal app, this is the right place to let the Cardinal developer know. Please create a new [issue](https://github.com/somebeaver/Cardinal-Project/issues/new) describing the problem if an issue for it doesn't already exist.

For general suggestions/feedback, [Reddit](https://old.reddit.com/r/cardinalapps) is a good place for discussion. You may also submit your feedback here on GitHub.

## Apps

The Cardinal project is comprised of different apps. Below is the plan for the ecosystem. Items in bold have been released, other items are either in development or planned for the future.

Name | Features | Platforms | Releases
------------ | ------------ | ------------- | ------------
**Cardinal Server** | [Web page](https://cardinalapps.xyz/en/cardinal-server) | **macOS**, **Windows**, Linux, Docker | [Downloads](https://github.com/somebeaver/Cardinal-Server)
**Cardinal Music** | [Web page](https://cardinalapps.xyz/en/cardinal-music) | **macOS**, **Windows**, Linux, mobile (PWA) | [Downloads](https://github.com/somebeaver/Cardinal-Music)
Cardinal Photos | TBA | macOS, Windows, Linux mobile (PWA) | -
Cardinal TV & Movies | TBA | macOS, Windows, Linux, mobile (PWA) | -
Cardinal Books | TBA | macOS, Windows, Linux, mobile (PWA) | -

## Tech Stack

Cardinal apps are built on top of Electron. Cardinal Server takes advantage of Electron multi-processing features for indexing, but the client apps are designed to run either in Electron or a regular browser. Each client app is a response PWA that, when running in Electron, can take advantage of system features (e.g., global keyboard shortcuts and file system access)
