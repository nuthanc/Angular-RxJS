### Repository

- https://github.com/DeborahK/angular-rxjs-signals-fundamentals
- Links of various topics: https://github.com/DeborahK/angular-rxjs-signals-fundamentals/blob/main/links.md

### Reactive Programming - Signals vs RxJS Observables

- Signals
  - Observe state(variable values)
  - Notify when the state changes
  - React to those Notifications
- RxJS Observables
  - Observe events or data that arrive over time
  - Notify when the event occurs or data is emitted
  - React to those Notifications

#### RxJS + Signals: Better Together

- RxJS works great for
  - Asynchronous operations such as HTTP requests
  - Retrieving and merging related sets of data
- Signal works great for
  - Managing data after it's been retrieved + computed signals
  - Binding in the tempate for better change detection
- So use RxJS for making API calls and then when you get the response, set the Signal and use it in the template

### RxJS

- Observe and React to Events through Time
- Converyor of Apples
  ![metaphor](img/rxjsMetaphor.png)

### Observable

- A collection of events or data values emitted over time
- Connects to a Source
- Emits notifications when it receives data or an event from the Source
- 3 types of Notificiations: next, error and complete

### Subscription

- An Observable must be subscribed to for it to emit values
- Unsubscribe to prevent memory leaks
- $ - convention for Observables
- Unsubscribe in ngOnDestroy

### Observer

- Observer is an object with 3 methods: next, error and complete
- observer is passed to the Observable's subscribe method

### Creating an Observable

- Creation functions: of, from, interval, timer, fromEvent

### Demo

- https://stackblitz.com/edit/rxjs-signals-m3-deborahk-bhnust?file=src%2Fmain.ts

### Operators

- Operators are functions that build on the observables
- Each Operator automatically subscribes to the Input Observable and returns a new Output Observable
- Minimize the number of operators -> To minimize operator setup and tear down, improving performance
- map - transform the values of each emission
- tap - taps into the emissions without affecting the item -> Used to perform side effects
- filter - filter the emissions based on a condition
- take - take the first n emissions and then complete
  - Insert take last if you want to take the specified number of emissions

### Retrieving Data with HTTP and Observables

- https://github.dev/DeborahK/angular-rxjs-signals-fundamentals
- Uses InMemoryWebApiModule for simulating a data server in app.config.ts

```ts
// Retrieve Products in ProductService
getProducts(): Observable<Product[]> {
  return this.http.get<Product[]>(this.productsUrl)
    .pipe(
      tap(data => console.log(data),
      catchError(this.handleError)
    ));
}

// In ProductList component
sub!: Subscription;
products: Product[] = [];

ngOnInit(): void {
  this.sub = this.productService.getProducts().subscribe(products => this.products = products);
}
```
- Strongly type the data and observable using the generic type parameters to minimize errors
- Use `provideHttpClient()` in app.config.ts to provide the the HttpClient Service and this import must be ahead of the InMemoryWebApiModule import