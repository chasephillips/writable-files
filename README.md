# Writable files
View proposals in the [EXPLAINER](EXPLAINER.md).

## Problem
Today, if a web site wants to create experiences involving local files (document editor, image compressor, etc.) they are at a disadvantage to native apps. A web site must ask the user to reopen a file every time they want to edit it. After opening, the site can only save changes by re downloading the file to the Downloads folder. A native app, by comparison, can maintain a most recently used list, auto save, and save files anywhere the user wants.

## Use cases
- Open local file to read
- Open local file to edit and then save
- Open local file to edit with auto save
- Create and save a new file
- Delete an existing file
- Read meta data about files

## Workarounds
- [FileSaver.js] polyfills `saveAs()` from the [W3C File API], but files open in a new window instead of downloading on Safari 6.1+ and iOS.
- In Edge, Firefox, and Chrome developers can:
	- Create a fake anchor element
	- Set the `download` attribute to the desired filename
	- Set `href:` to a data URI
	- Faking a click on the anchor element
- Setting `window.location` to `'data:application/octet-stream' + data_stream`
- Hidden Flash controls to display a “save as” dialog

These methods are clunky and only support “save as”. They do not support most recently used lists, auto save, save, or deleting a file. 