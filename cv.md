#Beata Maro

## Contact Information

**Email**: maro.beata@gmail.com <br>
**Telegram**: @beatamaro <br>
[Github](https://github.com/BeataMaro) <br>
[LinkedIn](https://www.linkedin.com/in/beata-maro-junior-web-developer/) <br>

## About me

I have been programming for 3 years and I have 5-months of commercial experience in programming online stores. I am a team player. It's important for me to be a value part of team. I am patient and persistent. This is why I am incredibly determined to never give up on finding solutions to difficult problems.
I am satisfied when the application takes shape.

What motivates me the most to continue my efforts are the visible effects of my work and the fact that my future projects can become useful to others.

## Skills

- HTML5
- CSS3
- SCSS
- JavaScript
- TypeScript

Basic:

- Angular
- React
- VueJs
- GIT 

## Code example

**RANDOM CODE GENERATOR**:

```
const DEFAULT_CHARSET =
  '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';

const roll = (min, max) => {
  let random = Math.floor(Math.random() * (max - min) + min);
  return random;
};

const generateCodeForm = document.getElementById('generateCodeForm');
const clearBtn = document.getElementById('clearBtn');
const generatedCodes = document.getElementById('generatedCodes');

let charset = [...DEFAULT_CHARSET];
let codes = [];

const generateCode = (ev) => {
  ev.preventDefault();
  generatedCodes.innerHTML = '';

  const formData = new FormData(ev.target);
  const formProps = Object.fromEntries(formData);

  let amountOfCodes = formProps.amountOfCodes || 1;
  let codeLength = formProps.codeLength || 3;
  let prefix = formProps.codePrefix.trim();
  let postfix = formProps.codePostfix.trim();
  formProps.setCharacterSet.length > 0
    ? (charset = [...formProps.setCharacterSet])
    : (charset = [...DEFAULT_CHARSET]);

  for (let j = 1; j <= amountOfCodes; j++) {
    let code = [];
    for (let i = 0; i <= codeLength - 1; i++) {
      let index = roll(0, charset.length - 1);
      let randomChar = charset[index];
      code.push(randomChar);
    }

    let completeCode = `${prefix}${code.join('')}${postfix}`;
    codes.push(completeCode);
  }

  codes.map((code) => {
    const codeDiv = document.createElement('p');
    codeDiv.textContent = code;
    generatedCodes.append(codeDiv);
  });
};

const clearForm = () => {
  generateCodeForm.reset();
  codes = [];
};

generateCodeForm.addEventListener('submit', generateCode);
clearBtn.addEventListener('click', clearForm);

```