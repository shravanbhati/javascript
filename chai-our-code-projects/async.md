# Chai our Code Async Projects
[Project Links](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

## Project 1 Solution: UnlimitedColors
```javascript
function colorChange() {
  let color = '#';
  const hex = '0123456789ABCDEF';

  for (i = 0; i < 6; i++) {
    const num = Math.floor(Math.random() * 16);
    color += hex[num];
  }
  return color;
}

const start = document.querySelector('#start');
const stop = document.querySelector('#stop');

let intervalID;
start.addEventListener('click', () => {
  if (!intervalID) {
    intervalID = setInterval(() => {
      document.querySelector('body').style.backgroundColor = colorChange();
    }, 1000);
  }
});

stop.addEventListener('click', () => {
  clearInterval(intervalID);
  intervalID = null; //memorey cleaning
});


```
## Project 2 Solution: keyboard
```javascript
const insert = document.querySelector('#insert');
window.addEventListener('keydown', (e) => {
  insert.innerHTML = `
  <div class='color'>
  <table>
  <tr>
    <th>Key</th>
    <th>KeyCode</th>
    <th>Code</th>
  </tr>
  <tr>
    <td>${e.key === ' ' ? 'space' : e.key}</td>
    <td>${e.keyCode}</td>
    <td>${e.code}</td>
  </tr>
</table>
  </div>
  `;
});

```
