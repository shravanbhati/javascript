# Chai our Code JavaScript Series DOM Projects

[Project Link](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

## Project 1 Solution: Color Changer
```javascript
const buttons = document.querySelectorAll('.button');
const body = document.querySelector('body');

// console.log(buttons);
buttons.forEach((button) => {
  // console.log(button);
  button.addEventListener('click', (e) => {
    console.log(e);
    console.log(e.target);
    if (e.target.id === 'grey') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'white') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'blue') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'yellow') {
      body.style.backgroundColor = e.target.id;
    }
  });
});

```

## Project 2 Solution: BMI Calculator

```javascript
const form = document.querySelector('form');

form.addEventListener('submit', (e) => {
  e.preventDefault();
  const height = parseInt(document.querySelector('#height').value);
  const weight = parseInt(document.querySelector('#weight').value);
  const results = document.querySelector('#results');

  if (height === '' || height < 0 || isNaN(height)) {
    results.innerHTML = `give a valid height ${height}`;
  } else if (weight === '' || weight < 0 || isNaN(weight)) {
    results.innerHTML = `give a valid weight ${weight}`;
  }
  const bmi = (weight / ((height * height) / 10000)).toFixed(2);
  results.innerHTML = `Your BMI is ${bmi}`;

  const msgDiv = document.createElement('div');
  let msg;

  if (bmi < 18.6) {
    msg = document.createTextNode(`You are under wieght :(`);
    console.log('1');
  } else if (bmi >= 18.6 && bmi <= 24.9) {
    msg = document.createTextNode(`Yore wieght is good :)`);
    console.log('2');
  } else {
    msg = document.createTextNode(`You are overwieght :(`);
    console.log('3');
  }

  msgDiv.appendChild(msg);
  results.appendChild(msgDiv);
});

```
## Project 3 Solution: Digital clock
```javascript
const clock = document.getElementById('clock');
setInterval(() => {
  let time = new Date();
  clock.innerHTML = time.toLocaleTimeString();
}, 1000);
```
## Project 4 Solution: Guess The Number
```javascript
let randomNum = parseInt(Math.random() * 100 + 1);
const userInput = document.querySelector('#guessField');
const submitBtn = document.querySelector('#subt');
const guessSlot = document.querySelector('.guesses');
const remainingGuess = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');

let prevGuess = [];
let numGuess = 1;

let playGame = true;
if (playGame) {
  submitBtn.addEventListener('click', (e) => {
    e.preventDefault();
    const guess = parseInt(userInput.value);
    inputValidation(guess);
  });
}

function inputValidation(guess) {
  if (isNaN(guess)) {
    alert('Please insert a vaild Number');
  } else if (guess <= 0) {
    alert('Please insert a value grater then 0');
  } else if (guess > 100) {
    alert('Please insert a value less then 100');
  } else {
    inputCheck(guess);
  }
}

function inputCheck(guess) {
  if (guess === randomNum) {
    displayMessage(`You Guessed it right, the number is ${randomNum}`);
    endGame(guess);
  } else if (guess > randomNum) {
    displayMessage(`Your guess is TOO Heigh`);
  } else if (guess < randomNum) {
    displayMessage(`Your guess is TOO Low`);
  }
  prevGuess.push(guess);
  guessSlot.innerHTML += `${guess},  `;
  numGuess++;
  remainingGuess.innerHTML = 11 - numGuess;

  if (numGuess === 11) {
    endGame(guess);
  }
}

function displayMessage(msg) {
  lowOrHi.innerHTML = `<h3>${msg}</h3>`;
  userInput.value = '';
}

function endGame(guess) {
  userInput.setAttribute('disabled', '');
  if (guess > randomNum || guess < randomNum) {
    displayMessage(`Game Over, right number was ${randomNum}`);
    numGuess = 1;
    remainingGuess.innerHTML = 11 - numGuess;
  }
  playGame = false;
  prevGuess = [];
  guessSlot.innerHTML = prevGuess;
  restartGame();
}

function restartGame() {
  userInput.removeAttribute('disabled');
  randomNum = parseInt(Math.random() * 100 + 1);
  playGame = true;
  numGuess = 1;
  remainingGuess.innerHTML = 11 - numGuess;
}

```
