---
title: API v1
parent: Extensions
---
# Extensions API V1
A quick list of the api YAB provides to all the extensions out of the box.

## Categories
```js
yab.browser // Contains info about all the current tabs active in the browser
yab.storage // storing and fetching information
yab.event // Events provided by YAB
yab.menu // interacting with the ui of the extension
yab.extension // current extension
```

## 1. Storage `yab.storage`
Sometimes extensions need to store information for later use. Generally this approach is preferred over storing information in a websites Local Storage, although this is completely possible too.
```js
yab.storage.set(key, data) // Sets info
yab.storage.get(key) // gets stuff
yab.storage.clear() // clears everything from the extensions storage
```

## 2. Browser and Tab Info/Actions `yab.browser`
This provides a lot of info especially about the tabs on the browser but also functionality:
```js
yab.browser.getTabs() // returns an array of ids of all the tabs that are currently open
yab.browser.version() // returns current browser version
yab.browser.uptime() // returns browser uptime in seconds
yab.browser.getProtocols() // gets all the currently available protocols and their info
yab.browser.addProtocol(name, data) // adds a new protocol
yab.browser.removeProtocol(name) // removes a protocol
yab.browser.getRAMUsage() // returns the browsers ram usage
yab.browser.focusTab(id) // focus on a certain tab
yab.browser.spawnTab(url) // spawns a tab to a given url
yab.browser.closeTab(id) // close a tab
yab.browser.reloadTab(id) // reloads a tab
yab.browser.getFocusedTab() // returns the id of the currently focused tab
yab.browser.muteTab(id) // mutes a tab
yab.browser.unmuteTab(id) // unmutes a tab
yab.browser.getTab(id) // returns an object with the info of the tab aswell as the document and much more
yab.browser.getProcess(id) // returns an object with the info of the backend process of a tab
```

## 3. Events `yab.event`
Provides various events to handle different situations
```js
yab.event.onTabLoad((id) => callback) // When a tab loads/is created, returns tab id
yab.event.onTabClosed((id) => callback) // when a tab closes
yab.event.onTabReloaded((id) => callback) // when a tab is reloaded
yab.event.onTabFocused((id) => callback) // when a tab is focused
yab.event.onTabBlurred((id,) => callback) // when a tab is blurred
yab.event.onTabNavigated((id) => callback) // when a tab goes to a new page
yab.event.onUpdate((update) => callback) // when the extension runs after being updated, returns update info
yab.event.onFirstRun(() => callback) // when its the first time the user runs this extension
```

## 4. Extension Menu `yab.menu`
Every extension is granted its own menu (enabled via the manifest file) thats reachable by the user by pressing the extensions icon typically located to the right of the seearchbar. Here an extension can show anything it wishes, including settings
```js
yab.menu.show // shows extension menu
yab.menu.hide // hides extension menu
yab.menu.toggle // toggles visiblity of the menu
yab.menu.isVisible // checks if a menu is visible
yab.menu.doc // the menu document to modify with js
```

## 5. Extension Info `yab.extension`
Provides some info about the extension itself
```js
yab.extension.checkForUpdates // checks for updates and gets the update. YAB should do this automatically though and this function will be deprecated soon
yab.extension.reload // reloads extension
yab.extension.id // the random id assigned to this extension by yab
yab.extension.name // the name of the extension
yab.extension.version // the current version of the extension
```
