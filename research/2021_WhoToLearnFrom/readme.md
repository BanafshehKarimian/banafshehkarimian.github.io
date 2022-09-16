## Advanced Usage

### Supporting legacy browsers (or IE11)

`<zero-md>` is based on [Custom Elements V1 specs](https://www.w3.org/TR/custom-elements/) which is
[natively](https://caniuse.com/custom-elementsv1) [supported](https://caniuse.com/shadowdomv1) in
all modern browsers - since at least **three** major versions ago across all vendors.
Correspondingly, there is therefore less need for
[web component polyfills](https://github.com/webcomponents/polyfills/tree/master/packages/webcomponentsjs).
However, while _not_ recommended, if there is a strong case to support legacy browsers, you can do
so like this:


### Specify your own URLs for Marked or Prism

By default, `<zero-md>` automatically loads the
[Markedjs](https://cdn.jsdelivr.net/gh/markedjs/marked@1/marked.min.js) and
[Prismjs](https://cdn.jsdelivr.net/gh/PrismJS/prism@1/prism.min.js) libraries from CDN. To use your
own URLs, do so like this:

### Append (or prepend) additional styles

You can _merge_ any additional style templates into an instance of `<zero-md>` like this:


### Dedent inline markdown

You can _opt-in_ to apply a dedent function onto the inline markdown. The function _tries_ to remove
the leading whitespace that would otherwise be incorrectly interpreted as a code block by the
markdown parser.


### Apply marked options during render
## test
### Append (or prepend) additional styles

You can _merge_ any additional style templates into an instance of `<zero-md>` like this:


### Dedent inline markdown

You can _opt-in_ to apply a dedent function onto the inline markdown. The function _tries_ to remove
the leading whitespace that would otherwise be incorrectly interpreted as a code block by the
markdown parser.


### Apply marked options during render
