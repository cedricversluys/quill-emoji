# Quill Emoji Selector
Module extension for [Quill.js](https://github.com/quilljs/quill) that handles emojis in the toolbar. Through this extension, you can add emojis through the toolbar at the top, or by typing the emoji code.

![Screenshot](/demo/screenshot.png)

To add an emoji via emoji code, type ``:`` followed by the first few letters, and an autocomplete menu will appear. You can then select or ``tab`` to the preferred emoji.




#### This module is still in active development

## Installation

```sh
yarn add quill-emoji
```

## Usage
### Webpack/ES6

```javascript
const toolbarOptions = {
  container: [
    ['bold', 'italic', 'underline', 'strike'],
    ['emoji'],   
  ],
  handlers: {'emoji': function() {}}
}
const quill = new Quill(editor, {
  // ...
  modules: {
    // ...
    toolbar: toolbarOptions,
    "emoji-toolbar": true,
    "emoji-textarea": true,
    "emoji-shortname": true,
  }
});
```
### Options
See [emoji-list.js](blob/master/src/emoji-list.js) for emoji list example

Sample options
```javascript
// Custom emoji-list
const emojiList = [ /* emojiList */ ];

// MDI emojicon instead of default icon
const emojiIcon = '<svg class="i" viewBox="0 0 24 24"><use href="#emoticon-happy"></use></svg>';

const quill = new Quill(editor, {
  // ...
  modules: {
    // ...
    "emoji-shortname": {
      emojiList: emojiList,
      fuse: {
        shouldSort: true,
        threshold: 0.1,
        location: 0,
        distance: 100,
        maxPatternLength: 32,
        minMatchCharLength: 1,
        keys: [
          "shortname"
        ]
      },
      onOpen: function() { /* ... */ },
      onClose: function(emojiListItem) { /* ... */ }
    },
    "emoji-toolbar": {
      buttonIcon: emojiIcon
    },
    "emoji-textarea": {
      buttonIcon: emojiIcon
    }
            
  }
});
```

## Contributing

Please check out our [contributing guidelines](CONTRIBUTING.md).
