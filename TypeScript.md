# TypeScript

Most of the contents are from https://basarat.gitbooks.io/typescript/


## [Promise](https://basarat.gitbooks.io/typescript/docs/promise.html)

- Any synchronous errors thrown in a `then` (or `catch`) result in the returned promise to fail:
```typescript
Promise.resolve(123)
    .then((res) => {
        throw new Error('something bad happened'); // throw a synchronous error
        return 456;
    })
    .then((res) => {
        console.log(res); // never called
        return Promise.resolve(789);
    })
    .catch((err) => {
        console.log(err.message); // something bad happened
    })
```

- Only the relevant (nearest tailing) `catch` is called for a given error (as the `catch` starts a new promise chain).
```typescript
Promise.resolve(123)
    .then((res) => {
        throw new Error('something bad happened'); // throw a synchronous error
        return 456;
    })
    .catch((err) => {
        console.log('first catch: ' + err.message); // something bad happened
        return 123;
    })
    .then((res) => {
        console.log(res); // 123
        return Promise.resolve(789);
    })
    .catch((err) => {
        console.log('second catch: ' + err.message); // never called
    })
```
