# Shadow Dom
Shadow DOM serves for encapsulation. It allows a component to have its very **own “shadow” DOM tree**, that **can’t be accidentally accessed from the main document**, may have **local style rules**, and more.

- Seprate DOM tree of element you can create which is not part of main document DOM, But when you render it's behave like a the part main document DOM

There are some bits of shadow DOM terminology to be aware of:
- **Shadow host:** The regular DOM node that the shadow DOM is attached to.
- **Shadow tree:** The DOM tree inside the shadow DOM.
- **Shadow boundary:** the place where the shadow DOM ends, and the regular DOM begins.
- **Shadow root:** The root node of the shadow tree.

#### Example 01
```html
<div id="shadowHost"></div>
```

```css
/* Global CSS not works inside shadow dom element*/
.shadow-dom-one {
  background: red;
}
```

```javascript
var host = document.querySelector('#shadowHost')
var shadowRoot = host.createShadowRoot()
var div = document.createElement('div')
div.textContent = "This is the Shadow DOM component"
div.className = "shadow-dom-one"
shadowRoot.appendChild(div)
```

#### Example 02
```html
<div id="shadowHost">Hello</div>
<template id="tmpl">
  <style>*{ color: red; }</style>
  <div>Hello <span class="name">I am a shodow Element</span></div>
</template>
<div>
```

```javascript
var host = document.querySelector('#shadowHost');
var shadowRoot = host.createShadowRoot();
shadowRoot.appendChild(document.querySelector('#tmpl').content)
```

**Example Link:** 
- https://codepen.io/suryansh54/pen/xxbQzaj
- https://codepen.io/suryansh54/pen/rNaQKQG
