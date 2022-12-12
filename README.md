# Accessibility Semantics CSS

A bookmarklet that adds annotations about semantics to your CSS.

- Be sure you are on [jmuheim.github.io](https://jmuheim.github.io/a11y-semantics-bookmarklet) (not [github.com/jmuheim](https://github.com/jmuheim/a11y-semantics-bookmarklet)), otherwise the text `A11y Semantics` in the next step will not be a link (due to  Github security restrictions).
- Drag this to your web browser's bookmarks bar: [A11y Semantics](javascript:(function()%7Bvar%20a%3Ddocument.getElementById(%22injected-css%22)%3Bnull%3D%3D%3Da%26%26(a%3Ddocument.createElement(%22link%22)%2Ca.id%3D%22injected-css%22%2Ca.rel%3D%22stylesheet%22%2Cdocument.getElementsByTagName(%22head%22)%5B0%5D.appendChild(a))%3Ba.href%3D%22https%3A%2F%2Fraw.githack.com%2FNothingAG%2Fa11y-semantics-css%2Fmaster%2Fa11y-semantics-visible.css%3Fv%3D%22%2BDate.now()%7D)()%3Bvoid+0)
- Go to any website you like, then click the created bookmark.

## Development

Use <https://www.yourjs.com/bookmarklet/> to create a bookmarklet from the following code, then update the above `A11y Semantics` link with the result.

```javascript
javascript: (function () {
  // Remove existing CSS, see https://dorward.uk/software/disablecss/#enhanced
  // for(i=0;i<document.styleSheets.length;i++) {
  // 	void(document.styleSheets.item(i).disabled=true);
  // }
  // el = document.getElementsByTagName('*');
  // for ( i=0; i<el.length; i++) {
  // 	void(el[i].style.cssText = '');
  // }

  // Inject semantics CSS, see https://gist.github.com/roura356a/65474d2fbf80d24911c9e817771ccaf8
  let cssLink = document.getElementById('injected-css');
  if (cssLink === null) {
    cssLink = document.createElement('link');
    cssLink.id = 'injected-css';
    cssLink.rel = 'stylesheet';
    document.getElementsByTagName('head')[0].appendChild(cssLink);
  }
  // Use githack.com to serve CSS with the correct Content-Type
  cssLink.href = 'https://raw.githack.com/NothingAG/a11y-semantics-css/master/a11y-semantics-visible.css?v=' + Date.now();
})();
```
