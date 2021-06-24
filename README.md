# WebComponentCheatSheet
A series of code snippets to make getting webcomponents up and running easier. Example code is typescript.


## Basic Template

No attributes or slots passed. Just a simple element with shadow dom.

```ts
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

## Using attributes

The easiest way to access attributes is with getters and setters. Here we place whatever's in the value into the center of a box.

```ts
export class IconButton extends HTMLElement {
  constructor() {
    super();
    this.attachShadow({ mode: "open" });
  }
  
  get value() {
    return this.getAttribute('value');
  }

  set value(newValue) {
    this.setAttribute('value', newValue);
  }

  connectedCallback() {
    this.shadowRoot.innerHTML = `
    <style>
      #container {
        width: 50px;
        height: 50px;
        display: grid;
        place-content: center;
        outline: 1px solid red;
      }
    </style>
    <div id = "container">
      <span> ${this.value} </span>
    </div>
   `;
  }
}

customElements.define("icon-button", IconButton);
```

```html
<icon-button value = 42> </icon-button>
```

![image](https://user-images.githubusercontent.com/6764693/123310644-4cc4b280-d4f4-11eb-9689-76261e612ce1.png)
