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
