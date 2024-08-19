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

## Анимация

```js
let squareX = 0;
let squareY = 0;
let squareWidth = 50;
let squareHeight = 50;
let squareSpeed = 2;

const canvas = document.getElementById('gamefield');

function draw() {
    // Сразу проверяем возможность использования канваса
    if (canvas.getContext) {
        const ctx = canvas.getContext('2d');
        // Очищаем канвас, необходимо для анимации
        ctx.clearRect(0, 0, canvas.width, canvas.height)
        ctx.fillStyle = 'rgb(200 0 0)';

        ctx.fillRect(squareX, squareY, squareWidth, squareHeight);
        squareY += squareSpeed;

        if (squareY + squareHeight > canvas.height || squareY < 0) {
            squareSpeed = -squareSpeed
        }

        requestAnimationFrame(draw)
    }
}

window.addEventListener('load', draw)
```
Тут мы выносим всю инфу о фигуре в переменные, чтобы иметь возможность использовать анимацию(?). 

**ОБЯЗАТЕЛЬНО**: очищаем канвас при помощи ```clearRect()``` для того, чтобы на каждый кадр канвас очищался и отрисовывал фигуру заново.

В этом примере красный квадрат будет двигаться вверх и вниз.
