---
title: Manifest v1
parent: Extensions
---
# Manifest v1
The manifest is a very simple json file that YAB uses to properly display your extensions and update it as soon as there is an update available. The typical structure would be:
```json
{
  "name": "Extension Name",
  "author": "John Doe",
  "id": "extension.unique.id",
  "description": "An Extension like no other.",
  "icon": "/assets/icon.png",
  "version": "1.0.0",
  "entry": "/index.html",
  "scripts": ["/script.js"]
}
```
As of now it consist of a couple simple elements: 
- `name` The name of your Extension and what is displayed to the user
- `author` The author of the Extension. You can write anything you want here
- `id` A unique id to differentiate from other extensions
- `description` The description of your Extension
- `icon` An icon that is 128 x 128 px
- `version` The version of the Extension
- `entry` The main html file
- `scripts` An array of script files

As of now this set up is very primitive but will be extended in the future if possible.

## FAQ - What to do if YAB is not updating your extensions automatically?
If you are certain that your extension is uploaded on the official repo for YAB Extensions remember that you need to increase the version in the manifest each time you make a change so YAB knows when a change has been made. 
YAB checks for updates by comparing the version number in your local extension with the one in the repository. If the version numbers are identical, YAB assumes the extension is already up to date — even if the code has changed.

## FAQ - Why aren't my scripts loading?
If this is happening to you it could be because of one of the following mistakes:
- you are adding the script by including it in the html instead of using the manifest file
- you used `"./"` instead of `"/"` when defining the paths of the scripts in the html
- you used `"../"`. We do not support relative paths, as to not allow extensions to escape their scope on the users machine
