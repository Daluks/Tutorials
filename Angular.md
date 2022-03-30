# Angular Guide

## Intro

* Reactive Single Page application
* Angular Versioning biggest change is AngularJS(Angular 1) -> Angular 2,4....13

### Angular Install and Setup

`` npm config set proxy=http://user:password@proxyAdress:portNumer ``

`` npm install @angular/cli``

### Bootstrap Install

`` npm install --save bpootstrap@3 ``

### TypeScript

* Offers more features than JavaScript(Types, Classes, Interfaces etc). Offers Strong Typing compared to vanilla JavaScript.
* Compiled to JavaScript

## Module

Start up uses the main.ts file which has a bootstrapModule method that passes and AppModule(referes to the file app.module).
In the file(app.module) we have a bootstrap array which references all the components(app.component.ts).
In the app.component.ts file we have the selector(app-root) which is in the index.html file.

### components

#### Creating a components

* Create component file (my.component.ts)

```
import { Component } from "@angular/core";

@Component({
    selector: 'app-server', //Selector is the reference tag for the html file
    templateUrl: './server.component.html' //points to is the file that will hold the components html content.
})
export class ServerComponent{

}
```

* Create components html file (my.component.html)
* Create components css file for custom styling (my.component.css)

#### AppModule

In the app module we add declaration of our Component

### Databinding

communication between business logic(typescript) and template(html)

* String interpolation ``{{data}})``
* Property binding ``[property]="data"``
* Event Binding ``(event)="expression"``
* combination of both (Two-way-binding) ``[(ngModel)]="data"``

#### String Interpolation

Declare the variable in TypeScript

``export class ServerComponent{
    serverId = 10;
    serverStatus = 'offline';
}``

Do the binding on the html

``<p>{{'server'}} with id {{serverId}} is {{serverStatus}}</p>``

#### Property Binding

``allowNewServer = false;``

``<button class="btn btn-primary" [disabled]="allowNewServer">``

#### Event Binding

* Part 1 OnClick and setting the value

``  onCreateServer(){
    this.servetrCreationStatus = 'server Created';
  }``

`` <button class="btn btn-primary" [disabled]="allowNewServer"(click)="onCreateServer()">Add server</button>``

* part 2 - On the input Updating and sending the value.

``
onUpdateServerName(event: any){
    this.serverName = (<HTMLInputElement>event.target).value;
  }
``

``
<input type="text" class="form-control" (input)="onUpdateServerName($event)">
``
#### Two-Way Binding

``<input type="text" class="form-control" [(ngModel)]="serverName"> ``

``<p>{{serverName}}</p>``

### Directives

Instructions in the DOM

#### ngIf with else usage (Structural Directives)

* Structural directive add or remove elements

``<ng-template #noServer><p>NoServer was created</p></ng-template>``

``<p *ngIf="serverCreated; else noServer">Server was created {{serverName}}</p>``

#### ngStyle (Attribute Directive, without a *)

* Attribute Directives are without a ``*``. They look like normal html attributes. They only change the element that they are placed on.

``<p [ngStyle]="{backgroundColor: getColor()}">{{'server'}} with id {{serverId}} is {{serverStatus}}</p>``
