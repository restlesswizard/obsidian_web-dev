---
title: Тег <canvas>
excerpt: Общая информация
---
`<canvas>` - тег из спецификации HTML5, внутри которого можно рисовать какую-нибудь графику при помощи JavaScript.

Базовый пример:

```js
function draw() {
    const canvas = document.getElementById('gamefield');

    if (canvas.getContext) {
        const ctx = canvas.getContext('2d');

        ctx.fillStyle = 'rgb(200 0 0)';
        ctx.fillRect(10, 10, 50, 50);
        
        ctx.fillStyle = 'rgb(0 0 200 / 50%)';
        ctx.fillRect(30, 30, 50, 50)
    }
}
draw()

window.addEventListener('load', draw)
```

```html
    <canvas id="gamefield" width="400" height="250"></canvas>
```