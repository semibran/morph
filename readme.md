# patch
> efficient patch operation for matching HTML elements to vnodes

```js
let element = document.createElement('h1')
element.innerText = 'hello world'
document.body.appendChild(element)

patch(element, {
  tag: 'h1',
  props: {},
  content: ['goodbye world']
})
```

## usage
[![https://nodei.co/npm/@semibran/patch.png?mini]][https://npmjs.com/package/@semibran/patch]

### `result = patch(elem, node)`
Alters the properties of `element` to match those specified by `node`, and returns `result`.

* `elem`: the `HTMLElement` to be patched
* `node`: a virtual node of the structure `{ tag, props, content }` against which `element` is compared

Note that if `element.tagName` and `node.tag` are different, `result` will be a brand new element. This behavior is caused by a property of the `HTMLElement` interface that prevents an element's tag from being changed once it is created. The only workaround is to create a new element to replace the old one, meaning that you may want to reset `element` to the return value of the `patch` function every time it is called if there is any chance of `node.tag` being changed. Otherwise, any changes you make to the new element will no longer be reflected onscreen.
