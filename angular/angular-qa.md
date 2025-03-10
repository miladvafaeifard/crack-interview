# Angular Tricky Questions and Answers

## 1. What is the difference between component and directive?

### **Components**:

- Are self-contained UI elements with their own template, logic, and styling
- Have their own lifecycle methods
- Can have input/output properties for data communication
- Generate DOM elements
- Are used when you need a complete UI feature with both display and logic

### **Directives**:

- Extend, modify or decorate existing DOM elements
- Don't have their own templates but manipulate host elements
- Come in three types: structural (e.g., *ngIf), attribute (e.g., [ngClass]), and custom
- Are used when you need to add behavior to existing elements

## 2. What are types of directives?

1. **Structural Directives**:
   - Change the DOM layout by adding/removing elements
   - Use an asterisk (*) prefix
   - Common examples: *ngIf, *ngFor, *ngSwitch
   - They manipulate DOM elements based on conditions or collections

2. **Attribute Directives**:
   - Change the appearance or behavior of existing elements
   - Don't change DOM structure, only modify the element they're attached to
   - Common examples: [ngClass], [ngStyle], [ngModel]
   - They're used like regular HTML attributes

3. **Custom Directives**:
   - User-defined directives created with @Directive decorator
   - Can be either structural or attribute type
   - Allow for reusable behaviors across components
   - Typically interact with the DOM using ElementRef, Renderer2, or HostListener

## 3. What are pipes?

Pipes in Angular are simple functions used to transform data in templates. They:

- Take input data and transform it to a desired output format
- Use the pipe (|) symbol in templates: `{{ value | pipeName:parameter }}`
- Can be chained: `{{ value | pipe1 | pipe2 }}`
- Come in two categories:
  - **Built-in pipes**: Such as DatePipe, UpperCasePipe, LowerCasePipe, CurrencyPipe, DecimalPipe, PercentPipe, AsyncPipe, etc.
  - **Custom pipes**: Created using the `@Pipe` decorator to implement custom transformations

- **Pure vs Impure pipes**: 
  - Pure pipes (default) are only executed when input value changes
  - Impure pipes (like AsyncPipe) can execute on every change detection cycle

- The AsyncPipe specifically subscribes to Observables or Promises and returns the latest value, automatically handling subscription and unsubscription

For example: `{{ dateValue | date:'short' }}` or `{{ observable$ | async }}`

Would you like to add anything to your answer or shall we move to the next question?

## 4. Angular Template Interpolation

In Angular templates, the double curly braces `{{ }}` represent interpolation, which is one of the most fundamental template syntax features.
What Interpolation Does:
- **Data Binding**: It binds data from your component class to the template (HTML)
- **Expression Evaluation**: It evaluates the JavaScript expression inside the braces and converts the result to a string

### **Examples**

```html
<!-- Simple property binding -->
<h1>Hello, {{ username }}</h1>

<!-- Expressions -->
<p>Total: {{ price * quantity }}</p>

<!-- Method calls -->
<div>{{ getFullName() }}</div>

<!-- Ternary operators -->
<span>{{ isActive ? 'Active' : 'Inactive' }}</span>

```

### **Important Notes**

- The expressions in `{{ }}` are executed in the context of the component instance
- Angular sanitizes the interpolated values to prevent XSS attacks
- You can't use assignments, `new`, `++`,`--`, etc. inside interpolation
- You can't use global JavaScript objects like window or document directly
- Angular updates the displayed value automatically when the bound data changes (part of change detection)

## 5. One way vs two way bindings

### **One-way binding:**
- Data flows in a single direction (either from component to view OR from view to component)
- Types of one-way binding:
  - **Property binding**: `[property]="value"` - Data flows from component to view (DOM)
  - **Event binding**: `(event)="handler()"` - Data flows from view (DOM) to component
  - **Interpolation**: `{{ value }}` - One-way from component to view
- @Input() decorator enables one-way binding from parent to child component

### **Two-way binding:**
- Data flows in both directions between component and view
- Uses the "banana in a box" syntax: `[(ngModel)]="property"`
- Is actually syntactic sugar that combines property binding and event binding:
  - `[(ngModel)]="property"` is equivalent to `[ngModel]="property" (ngModelChange)="property=$event"`
- Requires FormsModule to be imported for ngModel
- Can be implemented in custom components by combining @Input() property with an @Output() property named with the same name plus "Change" suffix

## 6. What are component lifecycle?

Angular provides 8 main lifecycle hooks, in order of execution:

1. **ngOnChanges**: Called when an input property changes (before ngOnInit and when input-bound property changes)
2. **ngOnInit**: Called once after the first ngOnChanges, when component is initialized
3. **ngDoCheck**: Called during every change detection run, allowing custom change detection
4. **ngAfterContentInit**: Called once after content (ng-content) has been projected into the component
5. **ngAfterContentChecked**: Called after every check of projected content
6. **ngAfterViewInit**: Called once after component's view and child views are initialized
7. **ngAfterViewChecked**: Called after every check of component's view and child views
8. **ngOnDestroy**: Called just before Angular destroys the component, useful for cleanup

Each hook corresponds to a lifecycle interface (e.g., OnInit, OnDestroy) that should be implemented by the component class.

For example:
```typescript
import { Component, OnInit, OnDestroy } from '@angular/core';

@Component({...})
export class MyComponent implements OnInit, OnDestroy {
  ngOnInit() {
    // Initialization logic
  }
  
  ngOnDestroy() {
    // Cleanup logic
  }
}
```

## 7. What types of forms presented in Angular?

### **Template-driven forms:**
- Use directives in the template to build the form
- Require FormsModule to be imported
- Form model is created implicitly by Angular
- Use ngModel, ngForm, and ngModelGroup directives
- Validation is primarily done through HTML attributes and directives
- More suitable for simple forms with basic validation
- Less explicit, as most logic is handled in the template
- Changes are tracked by Angular's two-way data binding

### **Reactive forms:**
- Form model is created explicitly in the component class
- Require ReactiveFormsModule to be imported
- Use FormControl, FormGroup, FormArray, and FormBuilder classes
- More robust for complex scenarios and dynamic forms
- Provide direct access to the form model for validation and testing
- Better for complex validation, dynamic form controls, and unit testing
- Offer better integration with RxJS because form controls are Observable
- Allow for more programmatic control and synchronous access to form data

Both approaches have their use cases, with template-driven being simpler but less flexible, and reactive being more powerful but requiring more code.

## 8. What is the difference between Observable and Subject?

### **Observable**
- An Observable is a "cold" data stream, meaning it starts emitting values only when a subscriber subscribes to it. Each subscriber gets an independent instance of the Observable.
- This makes Observables unicast by default, meaning each subscription maintains its own sequence of events without sharing state or emissions with other subscribers.

### **Subject**

- A Subject, on the other hand, is both an Observable and an Observer. It can subscribe to other Observables (acting as a consumer) and also multicast the emissions to its own subscribers.
- This makes it inherently "hot," as multiple subscribers will receive the same values simultaneously. A Subject allows for one-to-many streaming, where all subscribers get the same data at the same time.

## 9. Input and Output Decorators?

### **@Input() decorator:**
- Allows a child component to receive data from a parent component
- Creates a property that can be bound to in the parent component's template
- Data flows down from parent to child (unidirectional)
- Example syntax in child component: `@Input() item: string;`
- Used in parent template like: `<app-child [item]="parentData"></app-child>`
- Can have aliases: `@Input('aliasName') propertyName: type;`

### **@Output() decorator:**
- Allows a child component to emit events to the parent component
- Creates an EventEmitter property that the child can use to send data up
- Data flows up from child to parent through events
- Example syntax in child component: `@Output() itemChange = new EventEmitter<string>();`
- Child emits events: `this.itemChange.emit('new value');`
- Parent listens in template: `<app-child (itemChange)="handleChange($event)"></app-child>`

### **Together they enable:**
- Parent-child component communication
- Proper encapsulation of component functionality
- Implementation of reusable components
- Unidirectional data flow architecture (parent → child → parent)

Regarding change detection, OnPush strategy optimizes performance by only checking the component when inputs change by reference, rather than on every change detection cycle.

## 10. How Angular understands what dependency to use?

Angular uses a **Dependency Injection (DI)** system to provide dependencies to components, services, and other classes. Here's how it works:

1. **Registration**: Dependencies are registered with Angular's DI system using providers:
   - In NgModule's `providers` array
   - In Component's `providers` array (creating component-level instances)
   - Using the `@Injectable({providedIn: 'root'})` decorator for singleton services

2. **Injection Tokens**: Angular uses tokens (usually the class itself) to identify dependencies:
   - Class tokens: Most common, using the class constructor parameter type
   - String tokens: Less common, using InjectionToken for primitives
   - Injection tokens: For non-class dependencies

3. **Hierarchical Injector Tree**: Angular has a hierarchical injector system:
   - Root injector (application-wide)
   - NgModule injectors
   - Component injectors (and their child components)

4. **Resolution Process**: When a class requires a dependency:
   - Angular examines the constructor parameters and their types
   - It looks for providers starting at the current injector level
   - If not found, it moves up the injector hierarchy
   - If still not found, it throws an error

5. **Constructor Injection**: Dependencies are provided through constructor parameters:
```typescript
constructor(private http: HttpClient, private userService: UserService) { }
```

This system allows for efficient dependency management, testability through mocking, and proper separation of concerns.

## 11. Elements Tree vs Module Tree?

### **Elements Tree (Component Tree)**:
- Represents the hierarchy of components and DOM elements in an Angular application
- Starts with the root component (AppComponent) and branches out to all child components
- Each component has its own template that generates DOM elements
- The component tree directly maps to the rendered UI structure
- Angular's change detection works through this tree to update the UI
- Each component instance in the tree has its own lifecycle
- Components can communicate up and down this tree using @Input() and @Output()

### **Module Tree**:
- Represents the organization of NgModules in an application
- Starts with the root AppModule and includes feature modules, shared modules, etc.
- Defines the compilation context for components and the dependency injection hierarchy
- Modules can be eagerly loaded (at startup) or lazy loaded (on demand)
- Each module has its own injector that inherits from its parent module's injector
- Determines how services are scoped and shared across the application
- Affects how providers are resolved during dependency injection
- Lazy-loaded modules have their own child injector, creating isolation boundaries

The two trees are related but serve different purposes - the Elements/Component tree structures the UI, while the Module tree organizes code, defines compilation boundaries, and structures the dependency injection system.

## 12. Change Detection (CD) Strategies in Angular

1. **Default Strategy** (`ChangeDetectionStrategy.Default`):
   - Checks the entire component tree on any possible state change
   - Triggered by any of the following events:
     - DOM events (click, submit, etc.)
     - AJAX/HTTP requests
     - Timers (setTimeout, setInterval)
   - More predictable but less performant for large applications
   - Angular checks every binding in the component tree

2. **OnPush Strategy** (`ChangeDetectionStrategy.OnPush`):
   - Component is only checked when:
     - Input references change (not just their properties)
     - An event originated from the component or its children
     - Explicitly triggered with ChangeDetectorRef methods
     - Async pipe in the template emits a new value
   - More performant but requires immutable data patterns
   - Implemented by adding: `changeDetection: ChangeDetectionStrategy.OnPush` to component decorator

3. **Manual Change Detection Control**:
   - `ChangeDetectorRef.detectChanges()`: Triggers change detection for the component and its children
   - `ChangeDetectorRef.markForCheck()`: Marks component to be checked in the current or next change detection cycle
   - `ChangeDetectorRef.detach()`: Detaches component from change detection
   - `ChangeDetectorRef.reattach()`: Reattaches previously detached component

Zone.js is what enables automatic change detection by patching asynchronous browser APIs to notify Angular when to run change detection.

## 13. What is the difference between Observable and Promise?

### **Key differences between Observables and Promises:**

1. **Emission pattern:**
   - Promises: Emit a single value (resolve or reject) once
   - Observables: Can emit multiple values over time (stream)

2. **Execution:**
   - Promises: Eager execution (start doing work as soon as created)
   - Observables: Lazy execution (start only when subscribed to)

3. **Cancellation:**
   - Promises: Cannot be cancelled once created
   - Observables: Can be cancelled by unsubscribing

4. **Operators:**
   - Promises: Limited built-in functionality (then, catch, finally)
   - Observables: Rich set of operators for transformation, filtering, combination, etc.

5. **Error handling:**
   - Promises: One catch for all errors
   - Observables: Can handle errors and continue streaming

6. **Composition:**
   - Promises: Limited composition capabilities
   - Observables: Highly composable with operators like merge, concat, combineLatest

7. **Usage context:**
   - Promises: Better for one-time async operations (HTTP request, file read)
   - Observables: Better for streams of data or events (user inputs, WebSockets)

8. **API integration:**
   - Promises: Native to JavaScript
   - Observables: Part of RxJS library in Angular

The micro-task vs. macro-task distinction is more about how JavaScript schedules different types of asynchronous work, rather than being a fundamental difference between Promises and Observables.

## 14. What are different types of Subject in RxJs?

1. **Subject**:
   - Basic implementation that multicasts values to multiple subscribers
   - Doesn't store or replay any values
   - New subscribers only receive values emitted after they subscribe
   - Use case: Simple event bus when you don't need historical values

2. **BehaviorSubject**:
   - Requires an initial value and stores the latest value
   - New subscribers immediately receive the current/latest value
   - Use case: Representing "current" state that has a default value, like user settings or UI state

3. **ReplaySubject**:
   - Stores and replays a specified number of previous values to new subscribers
   - Can be configured with both buffer size and time window
   - Use case: When new subscribers need access to historical values, like recent user actions

4. **AsyncSubject**:
   - Only emits the final value to subscribers when the sequence completes
   - If the sequence doesn't complete, subscribers receive nothing
   - Use case: When only the final value matters, similar to Promise behavior

Each type has specific behaviors regarding:
- Whether they store values
- How many values they store
- When they emit to new subscribers
- How they handle completion

## 15. What are ways to pass data through Angular router?

1. **Route Parameters**:
   - Part of the route path: `/products/:id`
   - Defined in route configuration and accessed via ActivatedRoute
   ```typescript
   // Configuration
   { path: 'products/:id', component: ProductComponent }
   
   // Access in component
   this.route.paramMap.subscribe(params => {
     const id = params.get('id');
   });
   ```

2. **Query Parameters**:
   - Added to the URL after '?': `/products?category=electronics&sort=price`
   - Optional and don't affect route matching
   ```typescript
   // Navigation
   this.router.navigate(['/products'], { 
     queryParams: { category: 'electronics', sort: 'price' }
   });
   
   // Access in component
   this.route.queryParamMap.subscribe(params => {
     const category = params.get('category');
   });
   ```

3. **Route Data**:
   - Static data defined in route configuration
   ```typescript
   // Configuration
   { path: 'products', component: ProductsComponent, data: { title: 'Products List' } }
   
   // Access in component
   this.route.data.subscribe(data => {
     this.title = data.title;
   });
   ```

4. **Navigation Extras - State**:
   - Complex objects passed during navigation, not visible in URL
   ```typescript
   // Navigation
   this.router.navigate(['/products'], { 
     state: { product: productObject }
   });
   
   // Access in component
   const navigation = this.router.getCurrentNavigation();
   const state = navigation?.extras.state as { product: Product };
   ```

5. **Resolvers**:
   - Pre-fetch data before route activation
   ```typescript
   // Resolver
   @Injectable()
   export class ProductResolver implements Resolve<Product> {
     resolve(route: ActivatedRouteSnapshot): Observable<Product> {
       const id = route.paramMap.get('id');
       return this.productService.getProduct(id);
     }
   }
   
   // Configuration
   { path: 'product/:id', component: ProductComponent, resolve: { product: ProductResolver } }
   
   // Access in component
   this.route.data.subscribe(data => {
     this.product = data.product;
   });
   ```

Each approach has different use cases depending on data complexity, visibility requirements, and when the data needs to be available.

## 16. How SPA navigation different from MPA navigation

### **Multi-Page Application (MPA) Navigation:**
- Each request to the server results in a full page reload
- The browser completely discards the current page and loads the entire new page
- Server returns complete HTML for each new page
- Navigation triggers a complete browser refresh cycle
- Each page has its own URL
- Traditional web navigation model (e.g., traditional websites built with PHP, Ruby on Rails)
- Network-intensive as entire pages must be downloaded each time
- Browser history works naturally with back/forward buttons

**Single Page Application (SPA) Navigation:**
- Initial load of a single HTML page, then partial updates without full page reloads
- JavaScript intercepts navigation events and updates only parts of the page
- Uses AJAX/fetch to request only the data needed, not entire pages
- The page never fully reloads after initial load
- Client-side routing simulates navigation (Angular Router, React Router, etc.)
- More responsive user experience with faster transitions
- Less network traffic after initial load
- Requires client-side routing and state management
- Needs special handling for browser history (HTML5 History API)

**Key differences in user experience:**
- SPAs feel more like desktop applications with smoother transitions
- MPAs have the traditional web experience with visible page reloads
- SPAs typically have better performance after initial load
- MPAs may have faster initial page load (less JavaScript to parse)

**Technical differences:**
- SPAs handle routing on the client side
- MPAs handle routing on the server side
- SPAs require JavaScript for core functionality
- MPAs can work without JavaScript (with reduced functionality)

In Angular specifically, the Router module enables SPA navigation by changing what components are displayed without triggering full page reloads.

## 17. Optimization techniques within Angular?

Angular offers numerous optimization techniques to improve performance, reduce bundle size, and enhance user experience. Here's a comprehensive overview:

###  Build Optimization Techniques

1. **Production Build**
   - Use `ng build --prod` or `ng build --configuration=production` for AOT compilation, minification, and tree shaking
   - Enables dead code elimination and smaller bundle sizes

2. **Ahead-of-Time (AOT) Compilation**
   - Compiles templates during build instead of at runtime
   - Faster rendering and smaller bundle size
   - Catches template errors at build time

3. **Tree Shaking**
   - Removes unused code from final bundles
   - Works with ES modules to identify and eliminate dead code

4. **Code Splitting**
   - Lazy loading of feature modules: `loadChildren: () => import('./feature/feature.module').then(m => m.FeatureModule)`
   - Reduces initial bundle size by loading code on demand

5. **Differential Loading**
   - Generates separate bundles for modern and legacy browsers
   - Modern browsers get smaller, optimized code

### Runtime Optimization Techniques

6. **OnPush Change Detection**
   - `@Component({ changeDetection: ChangeDetectionStrategy.OnPush })`
   - Reduces change detection cycles by only checking components when inputs change

7. **Detaching Change Detector**
   - `this.changeDetectorRef.detach()` for components that rarely update
   - Manually control change detection with `detectChanges()`

8. **Pure Pipes**
   - Use pure pipes instead of methods in templates
   - Results are memoized, preventing recalculation

9. **TrackBy Function in ngFor**
   - `*ngFor="let item of items; trackBy: trackByFn"`
   - Improves rendering performance by helping Angular identify which items changed

10. **Virtual Scrolling**
    - Using `<cdk-virtual-scroll-viewport>` from Angular CDK
    - Renders only visible items in large lists

### Network Optimization

11. **Server-Side Rendering (SSR) with Angular Universal**
    - Improves initial load time and SEO
    - Pre-renders pages on the server

12. **Preloading Strategies**
    - Configure the router to preload modules in the background
    - `PreloadAllModules` or custom preloading strategies

13. **Progressive Web App (PWA) Support**
    - Add service workers with `ng add @angular/pwa`
    - Enables caching, offline functionality, and faster subsequent loads

### Bundle Size Optimization

14. **Removing Unused Dependencies**
    - Regular audit of package.json
    - Using tools like `npm-check` or `depcheck`

15. **Optimizing Third-Party Libraries**
    - Import only needed components from libraries
    - Consider smaller alternatives for large libraries

16. **Custom Webpack Configuration**
    - Fine-tune bundling process for specific needs
    - Split chunks more granularly

17. **Budget Configuration**
    - Set size budgets in angular.json
    - Fail builds that exceed size limits

### Memory Management

18. **Unsubscribing from Observables**
    - Prevent memory leaks by properly unsubscribing
    - Use `takeUntil`, `async` pipe, or explicit unsubscribe

19. **Avoiding Memory-Intensive Operations in Templates**
    - Move complex calculations to components
    - Cache results of expensive operations

20. **Optimizing Images and Assets**
    - Proper image formats and compression
    - Lazy loading of images

These optimization techniques can significantly improve Angular application performance when applied appropriately based on specific application needs and performance bottlenecks.