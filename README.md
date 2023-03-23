# MyStore
This is a simple demo to show the useage of angular.
## what is it
Angular is a framework to build web-applications.

## logic
Js works together with typescript (for the flavour) and this will intergrated in html.

### the basic files
several related files will be generated by `ng new my store`:
- index.html 
> contains all the the basic stuff of a html-file and in the body an tag named `<app-root></app-root>`
> that's the entrance for our components provided by angular
> here we can import some things like a libary as material by `<link></link>`-tags
- main.js
> contains the logic to bind a component and errorlogging
- styles.css 
> defines the global style
- src/app/app.component.html
> this is the root-file of html-file of other components. here all others can integrated by tags (`<top-bar></top-bar>`)


### components
A component in ts (can be generated by the cli `ng generate component test`) exists of 4 files:
- test.component.html = the "GUI" of the component
- test.component.css = the "look" of the component
- test.component.spec.ts = the related tests for the component
- test.component.ts = the *"logic"* of the component
### services
each component has its own space with logic located in the `*.ts`.

the communication between different components is managed by **services**. 

a service is a file (`*.service.ts`) which contains 'only' logic.

it is at the end a exported class which can imported by components.


## setup (angular project)
install angular by npm:
```bash
npm install -g @angular/cli
```bash
create new project with scss as css:
```bash
npx ng new my-store --style=scss
```

## cli common commands (with npx as prefix)
* `ng new`: Creates a new Angular workspace and initial application.
```
ng new MyStore
```
* `ng generate`: Generates components, directives, services, pipes, and other Angular artifacts.
  * `ng g c header` 
  * `ng g s courses` 
* `ng serve`: Compiles the application and serves it on a local development server.
* `ng build`: Compiles the application and creates a distributable package for deployment.
* `ng test`: Runs unit tests in the application.
* `ng e2e`: Runs end-to-end tests in the application.
* `ng lint`: Runs the linter to check for coding standards and best practices.
* `ng deploy`: Deploys the application to a hosting service, such as Firebase or GitHub Pages.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.
## Doings for this Demo
- `npm install @angular/cli`
> install angular with the cli local in this folder
- `npx ng new my-store --style=scss`
> create new project with scss as stylesheets
- `npx ng serve`
> start the server
- for the ability to use material-design import it by a `<link>`-tag to index.html in your root directory:
```html
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
```
- for the ability to use router import it in app.module.ts:
```ts
import { RouterModule } from '@angular/router';
```
- add it to the imports:
```ts
RouterModule.forRoot([
      { path: '', component: ProductListComponent },
    ])
  ],
```
- add custom styles to styles.css in the root directory:
```css
/* Global Styles */

* {
  font-family: 'Roboto', Arial, sans-serif;
  color: #616161;
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  margin: 0;
}

.container {
  display: flex;
  flex-direction: row;
}

router-outlet + *  {
  padding: 0 16px;
}

/* Text */

h1 {
  font-size: 32px;
}

h2 {
  font-size: 20px;
}

h1, h2 {
  font-weight: lighter;
}

p {
  font-size: 14px;
}

/* Hyperlink */

a {
  cursor: pointer;
  color: #1976d2;
  text-decoration: none;
}

a:hover {
  opacity: 0.8;
}

/* Input */

input {
  font-size: 14px;
  border-radius: 2px;
  padding: 8px;
  margin-bottom: 16px;
  border: 1px solid #BDBDBD;
}

label {
  font-size: 12px;
  font-weight: bold;
  margin-bottom: 4px;
  display: block;
  text-transform: uppercase;
}

/* Button */
.button, button {
  display: inline-flex;
  align-items: center;
  padding: 8px 16px;
  border-radius: 2px;
  font-size: 14px;
  cursor: pointer;
  background-color: #1976d2;
  color: white;
  border: none;
}

.button:hover, button:hover {
  opacity: 0.8;
  font-weight: normal;
}

.button:disabled, button:disabled {
  opacity: 0.5;
  cursor: auto;
}

/* Fancy Button */

.fancy-button {
  background-color: white;
  color: #1976d2;
}

.fancy-button i.material-icons {
  color: #1976d2;
  padding-right: 4px;
}

/* Top Bar */

app-top-bar {
  width: 100%;
  height: 68px;
  background-color: #1976d2;
  padding: 16px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

app-top-bar h1 {
  color: white;
  margin: 0;
}

/* Checkout Cart, Shipping Prices */

.cart-item, .shipping-item {
  width: 100%;
  min-width: 400px;
  max-width: 450px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 16px 32px;
  margin-bottom: 8px;
  border-radius: 2px;
  background-color: #EEEEEE;
}
```
- `npx ng g c top-bar`
> generate a component (header) for your app (top-bar.component.html, top-bar.component.scss, top-bar.component.ts, top-bar.component.spec.ts)
- content of top-bar.component.html:
```ts
<a [routerLink]="['/']">
  <h1>My Store</h1>
</a>
<a class="button fancy-button"><i class="material-icons">shopping_cart</i>Checkout</a>
```
- `npx ng g c product-list`
> generates product-list.component.ts (component). product-list.component.html (template), product-list.component.spec.ts (styles), product-list.spec.ts (tests) 
- use structural directives (`*ngFor`) [marked by *] to enable code (loops) within the html:
```ts
<div *ngFor="let product of products">
</div>
```
- use interpolation {{ }} to use code (variables) within html:
```html
  <h3>
      {{ product.name }}
  </h3>
```
- create a new file and insert data     
> `touch src/app/products.ts`
```ts
export interface Product {
  id: number;
  name: string;
  price: number;
  description: string;
}

export const products = [
  {
    id: 1,
    name: 'Phone XL',
    price: 799,
    description: 'A large phone with one of the best screens'
  },
  {
    id: 2,
    name: 'Phone Mini',
    price: 699,
    description: 'A great phone with one of the best cameras'
  },
  {
    id: 3,
    name: 'Phone Standard',
    price: 299,
    description: ''
  }
];
```
- import and use it in product-list.component.ts
> product-list.component.ts
```ts
import { products } from '../products'
...
export class ProductListComponent {
  products=products;
}
...
```
> product-list.component.html
```
...
  {{ product.name }}
...
```
- set an html attribut by [ ]
```ts
    <a [title]="product.name + ' details'">
```
- insert a condition in product-list.component.html:
```html
  <p *ngIf="product.description">
    Description: {{ product.description }}
  </p>
```
- add a button to the product-list.component.html
```html
<button type="button" (click)="share()">
    Share
  </button>
```
- create share()-function in product-list.component.ts
```ts
  share() {
    window.alert('The product has been shared!');
  }
```
- generate new component for alerts:
`npx ng g c product-alerts`
- make inputs possible in the product-alerts.component.ts:
```ts
import { Component, Input } from '@angular/core';
import { Product } from '../products';
```
- define a new property named product with an @Input() decorator:
```ts
export class ProductAlertsComponent {
  @Input() product!: Product;
}
```
- add a "Notify me"-button to product-alerts.component.html
```html
<p *ngIf="product && product.price > 700">
  <button type="button">Notify Me</button>
</p>
```
- make a communication between product-list and product-child possible (parent and child) with a new output in product-alerts.component.ts
```ts
import { Component, Input, Output, EventEmitter } from '@angular/core';
...
@Output() notify = new EventEmitter
```
- add this new function to the product-alerts.component.html
```ts
...
(click)="notify.emit()"
```
- add new function to product-list.component.ts to handle it
```ts
onNotify() {
    window.alert('You will be notified when the product goes on sale');
  }
```
- add the product-alerts-component to the product-list.component.html:
```html
<app-product-alerts
  [product]="product"> 
</app-product-alerts>
```
- add your new custom-event like an attribute to this component:
```html
  (notify)="onNotify()"
```
- generate new comoponent:
```bash
ng generate component product-details
```
- add a route for this component in app.module.ts
```ts
{ path: 'products/:productId', component: ProductDetailsComponent },
```
- add the link to the a-tag within product-list.component.html with a parameter:
```html
[routerLink]="['/products', product.id]">
```
- **most important:** in the `app.module.ts` is the definition/config of the router and we can access it by the `<router-outlet>`-tag
- add the router tag to the app.componet.html
```html
...
<router-outlet></router-outlet>
```
- in product-details.component.ts import of router and Products
```ts
import { Component, OnInit } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

import { Product, products } from '../products';
```
- define property:
```ts
export class ProductDetailsComponent implements OnInit {

  product: Product | undefined;
  /* ... */
}
```
- inject activatedRoute:
```ts
constructor(private route: ActivatedRoute) { }
```
- at the beginning of loading this componenet determine the product id
```ts
ngOnInit() {
  // First get the product id from the current route.
  const routeParams = this.route.snapshot.paramMap;
  const productIdFromRoute = Number(routeParams.get('productId'));

  // Find the product that correspond with the id provided in route.
  this.product = products.find(product => product.id === productIdFromRoute);
}
```
- fill the product-detail with content:
```html
<h2>Product Details</h2>

<div *ngIf="product">
  <h3>{{ product.name }}</h3>
  <h4>{{ product.price | currency }}</h4>
  <p>{{ product.description }}</p>
</div>
```
