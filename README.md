# WebComponentCheatSheet
A series of code snippets to make getting webcomponents up and running easier


## Basic Template

No attributes or slots passed. Just a simple element with shadow dom.

```js
export class MyElement extends HTMLElement {
  constructor() {
    super();
    this.attachShadow({ mode: "open" });
  }

  connectedCallback() {
    this.shadowRoot.innerHTML = `
    <style>
      #container {
        outline: 1px solid red;
      }
    </style>
    <div id = "container">
    </div>
   `;
  }
}

customElements.define("my-element", MyElement);
```

```html
<my-element></my-element>
```
