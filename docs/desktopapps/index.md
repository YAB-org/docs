---
title: Desktop Apps
nav_order: 3
---
# Desktop Apps
Sometimes you have a really cool website and would love to make an app version out of it , so the user doesnt have to open the browser each time they want to use your website. Well instead of having to develop the app all over again yab makes it really easy for you. 

By including only one simple json file on your website YAB will automatically allow users to "download" a desktop version of your website. This creates a shortcut on the users desktop that opens the website in its own window.

To include it simply add a script element to a json called `_yab_desktop.json`:

```json
{
  "name": "My Cool Website",
  "icon": "https...png",
  "rules": {
    "externalUrls": "browser",
    "allowDevTools": false
  },
  "window": {
    "theme": "#0000",
    "width": 800,
    "height": 600,
    "fullscreen": false
  } 
}
```
- `name` Name of the desktop shortcut
- `icon` Icon that appears when user launches app
- `rules` Opens any urls the user clicks on in yab. true allows user to open new sites in the same window. false disables all external urls from working.
- `externalUrls` "browser" opens any urls the user clicks on in yab. true allows user to open new sites in the same window. false disables all external urls from working.
- `allowDevTools` disable or enable yab dev tools
- `theme` the color of the window controls. Only works if user has setting "Use OS Native Window Controls" enabled in browser
- `width` width in px
- `height` height in px
- `fullscreen` launch fullscreen?

Some additional lua api exists to check if the website is running in the desktop environment:
```lua
if (browser._yab_.isPackaged) {}
```
To dynamically change the theme when possible, use:
```lua
browser._yab_.setTheme = "#0000" 
```
