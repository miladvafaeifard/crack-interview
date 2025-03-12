# ReactJs Tricky Questions and Answers

Sometimes, even with many years of experience in ReactJs, we encounter tricky questions that we can't answer expressively. To crack the interview, it's crucial to practice and write about these topics.

## Crucial Topics

### React Basics
- [What is React?](./questions.md#what-is-react)
- [What are the major features of React?](./questions.md#what-are-the-major-features-of-react)
- [What is JSX?](./questions.md#what-is-jsx)
- [Is it possible to use react without JSX?](./questions.md#is-it-possible-to-use-react-without-jsx)
- [What is the difference between Element and Component?](./questions.md#what-is-the-difference-between-element-and-component)
- [How to create components in React?](./questions.md#how-to-create-components-in-react)

### Event Handling and Props/State
- [How to bind methods or event handlers in JSX callbacks?](./questions.md#how-to-bind-methods-or-event-handlers-in-jsx-callbacks)
- [How to pass a parameter to an event handler or callback?](./questions.md#how-to-pass-a-parameter-to-an-event-handler-or-callback)
- [What are synthetic events in React?](./questions.md#what-are-synthetic-events-in-react)
- [What is state in React?](./questions.md#what-is-state-in-react)
- [What are props in React?](./questions.md#what-are-props-in-react)
- [What is the difference between state and props?](./questions.md#what-is-the-difference-between-state-and-props)
- [Why should we not update the state directly?](./questions.md#why-should-we-not-update-the-state-directly)
- [Is the state updated synchronously?](./questions.md#is-the-state-updated-synchronously)

### Keys, Refs and Memoization
- [What is the "key" prop and what is the benefit of using it in arrays of elements?](./questions.md#what-is-key-prop-and-what-is-the-benefit-of-using-it-in-arrays-of-elements)
- [What is the use of refs?](./questions.md#what-is-the-use-of-refs)
- [How to create refs?](./questions.md#how-to-create-refs)
- [React.memo vs useMemo](./questions.md#reactmemo-vs-usememo)
- [How do you memoize a component?](./questions.md#how-do-you-memoize-a-component)

### React DOM and Internals
- [What is Virtual DOM?](./questions.md#what-is-virtual-dom)
- [How Virtual DOM works?](./questions.md#how-virtual-dom-works)
- [What is the difference between Shadow DOM and Virtual DOM?](./questions.md#what-is-the-difference-between-shadow-dom-and-virtual-dom)
- [What is React Fiber?](./questions.md#what-is-react-fiber)
- [What is the main goal of React Fiber?](./questions.md#what-is-the-main-goal-of-react-fiber)

### React Lifecycle and Advanced Concepts
- [What are the different phases of component lifecycle?](./questions.md#what-are-the-different-phases-of-component-lifecycle)
- [What are the lifecycle methods of React?](./questions.md#what-are-the-lifecycle-methods-of-react)
- [What are Higher-Order components?](./questions.md#what-are-higher-order-components)
- [How to fetch data with React Hooks?](./questions.md#how-to-fetch-data-with-react-hooks)
- [What is context?](./questions.md#what-is-context)
- [What is children prop?](./questions.md#what-is-children-prop)
- [What is reconciliation?](./questions.md#what-is-reconciliation)
- [How do you conditionally render components?](./questions.md#how-do-you-conditionally-render-components)
- [What are error boundaries in React v16?](./questions.md#what-are-error-boundaries-in-react-v16)

### React Features and Rules
- [What are hooks?](./questions.md#what-are-hooks)
- [React hooks rules](./questions.md#react-hooks-rules)
- [What is Lifting State Up in React?](./questions.md#what-is-lifting-state-up-in-react)
- [What are fragments?](./questions.md#what-are-fragments)
- [Why fragments are better than container divs?](./questions.md#why-fragments-are-better-than-container-divs)

### Redux Basics
- [What is Flux?](./questions.md#what-is-flux)
- [What is Redux?](./questions.md#what-is-redux)
- [What hooks does Redux have?](./questions.md#what-hooks-does-redux-have)
- [What are the core principles of Redux?](./questions.md#what-are-the-core-principles-of-redux)
- [What are the downsides of Redux compared to Flux?](./questions.md#what-are-the-downsides-of-redux-compared-to-flux)
- [Can I dispatch an action in reducer?](./questions.md#can-i-dispatch-an-action-in-reducer)
- [How to access Redux store outside a component?](./questions.md#how-to-access-redux-store-outside-a-component)

### Redux Advanced
- [What is the difference between React context and React Redux?](./questions.md#what-is-the-difference-between-react-context-and-react-redux)
- [Should I keep all component's state in Redux store?](./questions.md#should-i-keep-all-components-state-in-redux-store)
- [What is the proper way to access Redux store?](./questions.md#what-is-the-proper-way-to-access-redux-store)
- [What is an action in Redux?](./questions.md#what-is-an-action-in-redux)
- [What is the purpose of the constants in Redux?](./questions.md#what-is-the-purpose-of-the-constants-in-redux)

### React Router
- [What is React Router?](./questions.md#what-is-react-router)
- [What hooks does React Router have?](./questions.md#what-hooks-does-react-router-have)
- [How React Router is different from history library?](./questions.md#how-react-router-is-different-from-history-library)

## Frequently asked questions

### React Fundamentals
- [What are Pure Components?](./questions.md#what-are-pure-components)
- [If Pure Component is better from the optimization point of view, why don't we use it by default?](./questions.md#if-pure-component-is-better-from-the-optimization-point-of-view-why-dont-we-use-it-by-default)
- [What is the purpose of the callback function as an argument of `setState()`?](./questions.md#what-is-the-purpose-of-the-callback-function-as-an-argument-of-setstate)
- [What are inline conditional expressions?](./questions.md#what-are-inline-conditional-expressions)

### React Basics
- [Difference between `createRef` and `useRef`](./questions.md#difference-between-createref-and-useref)
- [What are forward refs?](./questions.md#what-are-forward-refs)
- [What are controlled components?](./questions.md#what-are-controlled-components)
- [What are uncontrolled components?](./questions.md#what-are-uncontrolled-components)
- [Controlled vs Uncontrolled inputs](./questions.md#controlled-vs-uncontrolled-inputs)
- [What are portals in React?](./questions.md#what-are-portals-in-react)
- [What are stateless components?](./questions.md#what-are-stateless-components)
- [What are stateful components?](./questions.md#what-are-stateful-components)

### React Patterns
- [What is prop drilling?](./questions.md#what-is-prop-drilling)

### Redux Basics and Advanced
- [What is the difference between component and container in React Redux?](./questions.md#what-is-the-difference-between-component-and-container-in-react-redux)
- [What is Redux Thunk?](./questions.md#what-is-redux-thunk)
- [What are the drawbacks of MVW pattern?](./questions.md#what-are-the-drawbacks-of-mvw-pattern)
- [Are there any similarities between Redux and RxJS?](./questions.md#are-there-any-similarities-between-redux-and-rxjs)
- [How to dispatch an action on load?](./questions.md#how-to-dispatch-an-action-on-load)
- [How to use `connect` from React Redux?](./questions.md#how-to-use-connect-from-react-redux)
- [How to reset state in Redux?](./questions.md#how-to-reset-state-in-redux)
- [Why are Redux state functions called reducers?](./questions.md#why-are-redux-state-functions-called-reducers)
- [How to make an AJAX request in Redux?](./questions.md#how-to-make-an-ajax-request-in-redux)
- [What are the different ways to write `mapDispatchToProps()`?](./questions.md#what-are-the-different-ways-to-write-mapdispatchtoprops)
- [What is the use of the `ownProps` parameter in `mapStateToProps()` and `mapDispatchToProps()`?](./questions.md#what-is-the-use-of-the-ownprops-parameter-in-mapstatetoprops-and-mapdispatchtoprops)
- [How to structure Redux top-level directories?](./questions.md#how-to-structure-redux-top-level-directories)
- [How to set the initial state in Redux?](./questions.md#how-to-set-the-initial-state-in-redux)

### React Router
- [What are the components of React Router v4?](./questions.md#what-are-the-components-of-react-router-v4)
- [What is the purpose of push and replace methods of history?](./questions.md#what-is-the-purpose-of-push-and-replace-methods-of-history)
- [How do you programmatically navigate using React Router v4?](./questions.md#how-do-you-programmatically-navigate-using-react-router-v4)
- [How to get query parameters in React Router v4?](./questions.md#how-to-get-query-parameters-in-react-router-v4)
- [Why do you get "Router may have only one child element" warning?](./questions.md#why-do-you-get-router-may-have-only-one-child-element-warning)
- [How to pass params to `history.push` method in React Router v4?](./questions.md#how-to-pass-params-to-historypush-method-in-react-router-v4)
- [How to implement default or NotFound page?](./questions.md#how-to-implement-default-or-notfound-page)
- [How to get history on React Router v4?](./questions.md#how-to-get-history-on-react-router-v4)
- [How to perform automatic redirect after login?](./questions.md#how-to-perform-automatic-redirect-after-login)

## Good to know areas

### React Basics
- [What is the difference between createElement and cloneElement?](./questions.md#what-is-the-difference-between-createelement-and-cloneelement)
- [What is the purpose of using super constructor with props argument?](./questions.md#what-is-the-purpose-of-using-super-constructor-with-props-argument)
- [Why React uses className over class attribute?](./questions.md#why-react-uses-classname-over-class-attribute)
- [When to use a Class Component over a Function Component?](./questions.md#when-to-use-a-class-component-over-a-function-component)
- [What is the difference between HTML and React event handling?](./questions.md#what-is-the-difference-between-html-and-react-event-handling)

### Redux Basics
- [What is the difference between mapStateToProps() and mapDispatchToProps()?](./questions.md#what-is-the-difference-between-mapstatetoprops-and-mapdispatchtoprops)
- [What’s the purpose of the at symbol (`@`) in the Redux connect decorator?](./questions.md#whats-the-purpose-of-the-at-symbol--in-the-redux-connect-decorator)

### Redux Middleware
- [What is redux-saga?](./questions.md#what-is-redux-saga)
- [What is the mental model of redux-saga?](./questions.md#what-is-the-mental-model-of-redux-saga)
- [What are the differences between call and put in redux-saga?](./questions.md#what-are-the-differences-between-call-and-put-in-redux-saga)
- [What are the differences between redux-saga and redux-thunk?](./questions.md#what-are-the-differences-between-redux-saga-and-redux-thunk)

### Debugging Redux
- [What is Redux DevTools?](./questions.md#what-is-redux-devtools)
- [What are the features of Redux DevTools?](./questions.md#what-are-the-features-of-redux-devtools)

### Advanced Redux Concepts
- [What are Redux selectors and why to use them?](./questions.md#what-are-redux-selectors-and-why-to-use-them)
- [What is Redux Form?](./questions.md#what-is-redux-form)
- [What are the main features of Redux Form?](./questions.md#what-are-the-main-features-of-redux-form)

### Miscellaneous
- [How to add multiple middlewares to Redux?](./questions.md#how-to-add-multiple-middlewares-to-redux)
- [How Relay is different from Redux?](./questions.md#how-relay-is-different-from-redux)
