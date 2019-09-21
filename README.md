# holdon

helper functions for delaying

## Docs

https://puiutucutu.github.io/holdon/

## Usage

```
npm install holdon
```

## Examples

### delay

Promise example.

```js
import { delay } from "holdon";

// using promise syntax

// note, the callback inside the `then()` is a function,
// without it, the action would execute immediately
delay(2000).then(function() {
  console.log("done");
});

// this will execute immediately
delay(2000).then(console.log("executes immediately"));

//=> "executes immediately"
//=> "done" (after 2 seconds)
```

Async example.

```js
import { delay } from "holdon";

// using the async/await syntax
async function asyncExample() {
  await delay(2000);
  console.log("done (after awaiting delay)");
}

asyncExample();

//=> "done awaiting delay" (after 2 seconds)
```

### waitBefore

```js
import { waitBefore } from "holdon";

function sayHelloTo(name) {
  console.log(`hello ${name}`);
}
 
const waitTwoSeconds = waitBefore (2000);
const sayHelloAfterTwoSeconds = waitTwoSeconds (sayHelloTo);
 
sayHelloAfterTwoSeconds ("John"); //=> (after 2 seconds) "hello John"
 
// one liner
waitBefore (2) (sayHelloTo) ("John"); //=> (after 2 seconds) "hello John"
```