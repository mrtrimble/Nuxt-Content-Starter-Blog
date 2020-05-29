---
title: First Post!
summary: First post using the @nuxt/content module
author: Ryan Trimble
category: Javascript
publish_date: 1/1/2020

---

# Welcome

This is the first post using the @nuxt/component module!!


### Code Examples:
```js{1,3-5}[button-component.js]

const button = ( linkText, link ) => {
  //Create the button element
  const buttonElement = document.createElement('a')
  
  //Add the CSS Class to the element
  buttonElement.classList.add('btn')

  //Set the hypertext reference attribute and add the inner text
  buttonElement.setAttribute('href', link)
  buttonElement.innerText = linkText

  //Return the element
  return button;
}

```

### Embeddables:
<p class="codepen" data-height="612" data-theme-id="dark" data-default-tab="result" data-user="mrtrimble" data-slug-hash="WNQPXPb" style="height: 612px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="WNQPXPb">
  <span>See the Pen <a href="https://codepen.io/mrtrimble/pen/WNQPXPb">
  WNQPXPb</a> by Ryan Trimble (<a href="https://codepen.io/mrtrimble">@mrtrimble</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>