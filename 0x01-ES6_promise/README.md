# ES6 Promises

This project contains tasks for learning to use Promises in ECMAScript 2015 (ES6).

## Resources
Read or watch:

- [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [JavaScript Promise: An introduction](https://web.dev/promises/)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Throw / Try](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw)

## Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

- Promises (how, why, and what)
- How to use the then, resolve, catch methods
- How to use every method of the Promise object
- Throw / Try
- The await operator
- How to use an async function

## Requirements
- All your files will be executed on Ubuntu 18.04 LTS using NodeJS 12.11.x
- Allowed editors: vi, vim, emacs, Visual Studio Code
- All your files should end with a new line
- A README.md file, at the root of the folder of the project, is mandatory
- Your code should use the js extension
- Your code will be tested using Jest and the command npm run test
- Your code will be verified against lint using ESLint
- All of your functions must be exported

##Setup
Install NodeJS 12.11.x
(in your home directory):

```curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh```
```
sudo bash nodesource_setup.sh
sudo apt install nodejs -y
$ nodejs -v
v12.11.1
$ npm -v
6.11.3
```
## Install Jest, Babel, and ESLint
in your project directory:

- Install ```Jest using: npm install --save-dev jest```
- Install ```Babel using: npm install --save-dev babel-jest @babel/core @babel/preset-env @babel/cli```
- Install ```ESLint using: npm install --save-dev eslint```

## Files
- package.json
Click to show/hide file contents
- babel.config.js
Click to show/hide file contents
- utils.js
Use when you get to tasks requiring uploadPhoto and createUser.

Click to show/hide file contents
- .eslintrc.js
Click to show/hide file contents
and…
Don’t forget to run $ npm install when you have the package.json

Response Data Format
uploadPhoto returns a response with the format
```
{
  status: 200,
  body: 'photo-profile-1',
}
```
createUser returns a response with the format
```
{
  firstName: 'Guillaume',
  lastName: 'Salva',
}
```

## Tasks To Complete

## Task 0. **Keep every promise you make and only make promises you can keep**<br/>[0-promise.js](0-promise.js) contains a script that exports a function with the prototype `function getResponseFromAPI()`, which returns a Promise.

- Return a Promise using this prototype function getResponseFromAPI()
```
khalfan@aisha:~$ cat 0-main.js
import getResponseFromAPI from "./0-promise.js";

const response = getResponseFromAPI();
console.log(response instanceof Promise);

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 0-main.js 
true
khalfan@aisha:~$ 
```

## Task 1. **Don't make a promise...if you know you can't keep it**<br/>[1-promise.js](1-promise.js) 
contains a script that exports a function with the prototype `getFullResponseFromAPI(success)`, which returns a Promise. The parameter (`success`) is a `boolean`.
  + When the argument is:
    + `true`
      + Resolve the promise by passing an object with 2 attributes:
        + `status`: `200`
        + `body`: `'Success'`
    + `false`
      + Reject the promise with an error object with the message `The fake API is not working currently`.

- Try testing it out for yourself
```
khalfan@aisha:~$ cat 1-main.js
import getFullResponseFromAPI from './1-promise';

console.log(getFullResponseFromAPI(true));
console.log(getFullResponseFromAPI(false));

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 1-main.js 
Promise { { status: 200, body: 'Success' } }
Promise {
  <rejected> Error: The fake API is not working currently
    ...
    ...
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 1-promise.js

## Task 2. **Catch me if you can!**
<br/>[2-then.js](2-then.js) contains a script that exports a function with the prototype `function handleResponseFromAPI(promise)`, which appends three handlers to the `promise` argument.
Using the function prototype below

`function handleResponseFromAPI(promise`)
Append three handlers to the function:
  + When the Promise resolves, return an object with the following attributes:
    + `status`: `200`,
    + `body`: `'success'`
  + When the Promise rejects, return an empty `Error` object.
  + For every resolution, log `Got a response from the API` to the console.

```
khalfan@aisha:~$ cat 2-main.js
import handleResponseFromAPI from "./2-then";

const promise = Promise.resolve();
handleResponseFromAPI(promise);

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 2-main.js 
Got a response from the API
khalfan@aisha:~$ 
Repo:
```
- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 2-then.js

## Task 3. **Handle multiple successful promises**<br/>[3-all.js](3-all.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Knowing that the functions in `utils.js` return promises, use the prototype below to collectively resolve all promises and log `body firstName lastName` to the console.
  + Use the prototype below to collectively resolve all promises and log `body firstName lastName` to the console. The functions in [utils.js](utils.js) return Promises.
    ```js
    function handleProfileSignup()
    ```
  + In the event of an error, log `Signup system offline` to the console.

```
khalfan@aisha:~$ cat 3-main.js
import handleProfileSignup from "./3-all";

handleProfileSignup();

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 3-main.js 
photo-profile-1 Guillaume Salva
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 3-all.js

## Task 4. **Simple promise**<br/>[4-user-promise.js](4-user-promise.js) contains a script that exports a function with the prototype `function signUpUser(firstName, lastName)`,
That returns a resolved promise with the object shown below.
  ```js
  {
    firstName: value,
    lastName: value,
  }
  ```
```
khalfan@aisha:~$ cat 4-main.js
import signUpUser from "./4-user-promise";

console.log(signUpUser("Bob", "Dylan"));

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 4-main.js 
Promise { { firstName: 'Bob', lastName: 'Dylan' } }
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 4-user-promise.js

## Task 5. **Reject the promises** <br/>[5-photo-reject.js](5-photo-reject.js) contains a script that exports a function with the prototype `function uploadPhoto(filename)`, which returns a Promise rejecting with an Error and the string `$fileName cannot be processed`, where `fileName` is a string.

## Task 6. **Handle multiple promises**<br/>[6-final-user.js](6-final-user.js) contains a script that meets the following requirements.
  + Import `signUpUser` from [4-user-promise.js](4-user-promise.js) and `uploadPhoto` from [5-photo-reject.js](5-photo-reject.js).
  + Export a function named `handleProfileSignup` that accepts three arguments `firstName` (string), `lastName` (string), and `fileName` (string) and calls the two other functions (`signUpUser` and `uploadPhoto`).
  + When the promises are all settled it should return an array with the following structure:
    ```js
    [
      {
        status: status_of_the_promise,
        value: value || reason // value or error returned by the Promise
      },
      ...
    ]
    ```

## Task 7. **Load balancer**<br/>[7-load_balancer.js](7-load_balancer.js) contains a script that exports a function with the prototype `function loadBalancer(chinaDownload, USDownload)`, which returns the value returned by the promise that resolved the first, where `chinaDownload` and `USDownload` are Promises.

## Task 8. **Throw error / try catch**<br/>[8-try.js](8-try.js) contains a script that meets the following requirements.
  + Exports a function with the prototype `function divideFunction(numerator, denominator)`, where `numerator` and `denominator` are numbers.
  + When the `denominator` argument is equal to 0, the function should throw a new error with the message `cannot divide by 0`.
  + Otherwise it should return the `numerator` divided by the `denominator`.

## Task 9. **Throw an error**<br/>[9-try.js](9-try.js) contains a script that meets the following requirements.
  + Export a function named `guardrail` that accepts a function argument called `mathFunction`.
  + The `guardrail` function should create and return an array named `queue`.
  + When the `mathFunction` function is executed, the value returned by the function should be appended to the `queue`. If this function throws an error, the error message should be appended to the `queue`.
  + In every case, the message `Guardrail was processed` should be added to the queue.

## Task 10. **Await / Async**<br/>[100-await.js](100-await.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Export an async function named `asyncUploadUser` that will call the two functions imported above and return an object with the following format:
    ```js
    {
      photo: response_from_uploadPhoto_function,
      user: response_from_createUser_function,
    }
    ```
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + If one of the async function fails, return an empty object as shown below:
    ```js
    {
      photo: null,
      user: null,
    }
    ``# ES6 Promises

This project contains tasks for learning to use Promises in ECMAScript 2015 (ES6).

## Resources
Read or watch:

- [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [JavaScript Promise: An introduction](https://web.dev/promises/)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Throw / Try](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw)

## Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

- Promises (how, why, and what)
- How to use the then, resolve, catch methods
- How to use every method of the Promise object
- Throw / Try
- The await operator
- How to use an async function

## Requirements
- All your files will be executed on Ubuntu 18.04 LTS using NodeJS 12.11.x
- Allowed editors: vi, vim, emacs, Visual Studio Code
- All your files should end with a new line
- A README.md file, at the root of the folder of the project, is mandatory
- Your code should use the js extension
- Your code will be tested using Jest and the command npm run test
- Your code will be verified against lint using ESLint
- All of your functions must be exported

##Setup
Install NodeJS 12.11.x
(in your home directory):

```curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh```
```
sudo bash nodesource_setup.sh
sudo apt install nodejs -y
$ nodejs -v
v12.11.1
$ npm -v
6.11.3
```
## Install Jest, Babel, and ESLint
in your project directory:

- Install ```Jest using: npm install --save-dev jest```
- Install ```Babel using: npm install --save-dev babel-jest @babel/core @babel/preset-env @babel/cli```
- Install ```ESLint using: npm install --save-dev eslint```

## Files
- package.json
Click to show/hide file contents
- babel.config.js
Click to show/hide file contents
- utils.js
Use when you get to tasks requiring uploadPhoto and createUser.

Click to show/hide file contents
- .eslintrc.js
Click to show/hide file contents
and…
Don’t forget to run $ npm install when you have the package.json

Response Data Format
uploadPhoto returns a response with the format
```
{
  status: 200,
  body: 'photo-profile-1',
}
```
createUser returns a response with the format
```
{
  firstName: 'Guillaume',
  lastName: 'Salva',
}
```

## Tasks To Complete

## Task 0. **Keep every promise you make and only make promises you can keep**<br/>[0-promise.js](0-promise.js) contains a script that exports a function with the prototype `function getResponseFromAPI()`, which returns a Promise.

- Return a Promise using this prototype function getResponseFromAPI()
```
khalfan@aisha:~$ cat 0-main.js
import getResponseFromAPI from "./0-promise.js";

const response = getResponseFromAPI();
console.log(response instanceof Promise);

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 0-main.js 
true
khalfan@aisha:~$ 
```

## Task 1. **Don't make a promise...if you know you can't keep it**<br/>[1-promise.js](1-promise.js) 
contains a script that exports a function with the prototype `getFullResponseFromAPI(success)`, which returns a Promise. The parameter (`success`) is a `boolean`.
  + When the argument is:
    + `true`
      + Resolve the promise by passing an object with 2 attributes:
        + `status`: `200`
        + `body`: `'Success'`
    + `false`
      + Reject the promise with an error object with the message `The fake API is not working currently`.

- Try testing it out for yourself
```
khalfan@aisha:~$ cat 1-main.js
import getFullResponseFromAPI from './1-promise';

console.log(getFullResponseFromAPI(true));
console.log(getFullResponseFromAPI(false));

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 1-main.js 
Promise { { status: 200, body: 'Success' } }
Promise {
  <rejected> Error: The fake API is not working currently
    ...
    ...
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 1-promise.js

## Task 2. **Catch me if you can!**
<br/>[2-then.js](2-then.js) contains a script that exports a function with the prototype `function handleResponseFromAPI(promise)`, which appends three handlers to the `promise` argument.
Using the function prototype below

`function handleResponseFromAPI(promise`)
Append three handlers to the function:
  + When the Promise resolves, return an object with the following attributes:
    + `status`: `200`,
    + `body`: `'success'`
  + When the Promise rejects, return an empty `Error` object.
  + For every resolution, log `Got a response from the API` to the console.

```
khalfan@aisha:~$ cat 2-main.js
import handleResponseFromAPI from "./2-then";

const promise = Promise.resolve();
handleResponseFromAPI(promise);

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 2-main.js 
Got a response from the API
khalfan@aisha:~$ 
Repo:
```
- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 2-then.js

## Task 3. **Handle multiple successful promises**<br/>[3-all.js](3-all.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Knowing that the functions in `utils.js` return promises, use the prototype below to collectively resolve all promises and log `body firstName lastName` to the console.
  + Use the prototype below to collectively resolve all promises and log `body firstName lastName` to the console. The functions in [utils.js](utils.js) return Promises.
    ```js
    function handleProfileSignup()
    ```
  + In the event of an error, log `Signup system offline` to the console.

```
khalfan@aisha:~$ cat 3-main.js
import handleProfileSignup from "./3-all";

handleProfileSignup();

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 3-main.js 
photo-profile-1 Guillaume Salva
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 3-all.js

## Task 4. **Simple promise**<br/>[4-user-promise.js](4-user-promise.js) contains a script that exports a function with the prototype `function signUpUser(firstName, lastName)`,
That returns a resolved promise with the object shown below.
  ```js
  {
    firstName: value,
    lastName: value,
  }
  ```
```
khalfan@aisha:~$ cat 4-main.js
import signUpUser from "./4-user-promise";

console.log(signUpUser("Bob", "Dylan"));

khalfan@aisha:~$ 
khalfan@aisha:~$ npm run dev 4-main.js 
Promise { { firstName: 'Bob', lastName: 'Dylan' } }
khalfan@aisha:~$ 
```
Repo:

- GitHub repository: alx-backend-javascript
- Directory: 0x01-ES6_promise
- File: 4-user-promise.js

## Task 5. **Reject the promises** <br/>[5-photo-reject.js](5-photo-reject.js) contains a script that exports a function with the prototype `function uploadPhoto(filename)`, which returns a Promise rejecting with an Error and the string `$fileName cannot be processed`, where `fileName` is a string.

## Task 6. **Handle multiple promises**<br/>[6-final-user.js](6-final-user.js) contains a script that meets the following requirements.
  + Import `signUpUser` from [4-user-promise.js](4-user-promise.js) and `uploadPhoto` from [5-photo-reject.js](5-photo-reject.js).
  + Export a function named `handleProfileSignup` that accepts three arguments `firstName` (string), `lastName` (string), and `fileName` (string) and calls the two other functions (`signUpUser` and `uploadPhoto`).
  + When the promises are all settled it should return an array with the following structure:
    ```js
    [
      {
        status: status_of_the_promise,
        value: value || reason // value or error returned by the Promise
      },
      ...
    ]
    ```

## Task 7. **Load balancer**<br/>[7-load_balancer.js](7-load_balancer.js) contains a script that exports a function with the prototype `function loadBalancer(chinaDownload, USDownload)`, which returns the value returned by the promise that resolved the first, where `chinaDownload` and `USDownload` are Promises.

## Task 8. **Throw error / try catch**<br/>[8-try.js](8-try.js) contains a script that meets the following requirements.
  + Exports a function with the prototype `function divideFunction(numerator, denominator)`, where `numerator` and `denominator` are numbers.
  + When the `denominator` argument is equal to 0, the function should throw a new error with the message `cannot divide by 0`.
  + Otherwise it should return the `numerator` divided by the `denominator`.

## Task 9. **Throw an error**<br/>[9-try.js](9-try.js) contains a script that meets the following requirements.
  + Export a function named `guardrail` that accepts a function argument called `mathFunction`.
  + The `guardrail` function should create and return an array named `queue`.
  + When the `mathFunction` function is executed, the value returned by the function should be appended to the `queue`. If this function throws an error, the error message should be appended to the `queue`.
  + In every case, the message `Guardrail was processed` should be added to the queue.

## Task 10. **Await / Async**<br/>[100-await.js](100-await.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Export an async function named `asyncUploadUser` that will call the two functions imported above and return an object with the following format:
    ```js
    {
      photo: response_from_uploadPhoto_function,
      user: response_from_createUser_function,
    }
    ```
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + If one of the async function fails, return an empty object as shown below:
    ```js
    {
      photo: null,
      user: null,
    }
    ````
