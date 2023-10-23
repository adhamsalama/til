https://stackoverflow.com/questions/46914025/node-exits-without-error-and-doesnt-await-promise-event-callback

This works normally
```js
async function connectToDatabase(config = {}) {
  if (!config.port) return;
  return new Promise((resolve) => {
    resolve();
  });
}

(async function main() {
  console.log("STARTED");
  await connectToDatabase(); // Anything after this line will be executed
  console.log("CONNECTED");
  console.log("DOING SOMETHING ELSE");
})();
```

Anything after await won't be executed
```js
async function connectToDatabase(config = {}) {
  return new Promise((resolve) => {
    if (!config.port) return;
    resolve();
  });
}

(async function main() {
  console.log("STARTED");
  await connectToDatabase(); // Anything after this line won't be executed
  console.log("CONNECTED");
  console.log("DOING SOMETHING ELSE");
})();
```
