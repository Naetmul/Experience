# ReactiveX

https://www.youtube.com/watch?v=QdmkXL7XikQ

### Threading
- `subscribeOn()` affects thinkgs upstream, and flows next.
- If there exist multiple `subscribeOn()`s, then the first one wins.
```java
Observable.just("Hello")                        // Executed in io()
        .subscribeOn(Schedulers.io())
        .map()                                  // Executed in io()
        .subscribeOn(Schedulers.computation())
        .subscribe();                           // Executed in io()
```

- `observeOn()` affects below it.
- `observeOn()` can be called multiple times.
```java
Observable.just("Hello")                        // Executed in the current thread
        .observeOn(Schedulers.io())
        .map()                                  // Executed in io()
        .observeOn(Schedulers.computation())
        .subscribe();                           // Executed in computation()
```

### Schedulers
https://stackoverflow.com/questions/31276164/rxjava-schedulers-use-cases
