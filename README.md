# Scrummer [![Build Status](https://travis-ci.org/rickpastoor/scrummer.svg?branch=master)](https://travis-ci.org/rickpastoor/scrummer)

[Download Scrummer for Google Chrome](https://chrome.google.com/webstore/detail/scrummer/pmoipljemkkfadmmoenedgfepbefafnp)

[Download Scrummer for Firefox](https://addons.mozilla.org/en-US/firefox/addon/scrummer-1/)

[Download Scrummer for Safari](https://github.com/rickpastoor/scrummer/releases/latest)

I'm working with Trello. A lot. I've used the [Scrum for Trello plugin](https://github.com/Q42/TrelloScrum), but I found
it slowing down Trello when working with a lot of cards. So I wrote a new plugin
from scratch, without dependencies on external libraries to keep the footprint as
small as possible. Using native browser API's instead of jQuery makes it lightning-fast!

Big kudo's to the guys at Q42 for building Scrum for Trello. If you want more features,
use theirs. Use this plugin if you just want to keep track of storypoints and totals
for each column in your board, nothing else.

## Features

* Displays the number of points for each card in a badge
* Total points for each column
* Clickable buttons next to the title-field to quickly enter your estimate
* Ability to create a separator card that will count the points starting from the top or the previous separator card for easy planning

## Separators

Sketching out your sprints is pretty hard, just like planning in general. I found myself counting points during planning and refinement sessions to see how much work can be done in one sprint. Scrummer now has a feature to help you with this: separators.

Add a new card with the contents `#!!` anywhere in your board. It will count the points that are added to the card above it. You can add multiple separators in a single column: it will always start counting from the separator above. This allows you to prepare your sprints in advance, all within your Trello board.

You can also attach a name to a separator, by simply adding it after the `#!!` tag. E.g.: `#!! 1.0 release`.

## Developing and testing Chrome

To get started with developing your own additions to this plugin, run this command:

```
tools/make-chromium.sh
```

After this, add a new unpacked extension to your local Google Chrome and point this to the `dist/build/scrummer.chromium` folder. Now make your changes, run `make-chromium` and refresh your plugin
in Chrome to see if everything is working as it should. There are no tests yet, because YOLO.

## Developing and testing Firefox

To get started with developing your own additions to this plugin, run this command:

```
tools/make-firefox.sh
```

After this, install JPM:

```
npm install jpm --global
```

With JPM, you can run the plugin in a debug environment. Change your directory to `dist/build/scrummer.firefox` and run `jpm run`. Now open your Trello board to see if your changes are working as expected. Happy coding!

## Developing and testing Safari

To build your own version of the Scrummer for Safari plugin, follow these steps:

Install xar-js:

```
npm intall xar-js --global
```

You need to [follow the xar-js README](https://github.com/robertknight/xar-js#building-a-safari-extension) on how to export the required certificate files
in order to build a valid version of the extension.

After following this guide, you should have these files inside your `platform/safari` folder:

| Filename               |
|:-----------------------|
| apple-intermediate.pem |
| apple-root.pem         |
| cert.pem               |
| privatekey.pem         |

Almost ready. Now run this command:

```
tools/make-safari.sh all
```

The script will build a `scrummer.safariextz`. Doubleclick it and Safari will ask you if you want to install the extension.
