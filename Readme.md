# Getting started

### Install Angular on NixOS

* check `default.nix` which is prepared for the `nix-shell`

0. check Angular version after installing: `$ ng --version`
1. new project: `$ ng new <project-name>`
2. view it move to project dir and: `$ ng serve`
3. check typescript version: `$ tsc --version`

* getting started with typescript 
* typescript folder includes mini .ts tutorial

### Components in Angular (encapsulates Data, Logic, HTML-Template)
#### Steps to approach:
1. Create component (like i did with: courses.component.ts)
2. Register it in a module (add it to app.moudle.ts)
3. Add an element in an HTML markup (add component to app.component.html)

* another approach would be to create the component automatically
    1.  `$ ng g c course` (g = generate, c = component) this creates a whole folder with all needed components
    2. done!

### Modify the DOM
```
import { Component } from '@angular/core';

@Component({
    selector: 'courses', //selector in DOM tree
    template: `
    <h2>{{ title }}</h2>
    <ul>
        <li *ngFor="let course of courses">   
            {{ course }}
        </li>
    </ul> 
    
    ` 
})
export class CoursesComponent {
    title = 'List of courses';
    courses = ["course1", "course2", "course3"];

    getTitle() {
        return this.title;
    }
}
```

the `*` is used when you want to modify something in the DOM. Here it is done by a Angular for-loop

### Services (Request HTTP Enpoint to get data from a server for example)
A service and its logic should be separated from the components code, which only should be responsible 
for the view of the elements. Furthermore a service is a plain typscript class so it has no Angular
decorator. 

#### To make the class better testable (for instance with mock objects) use DI whenever possible.
So in the class which is consuming the service....:
```
    constructor() {
        let service = new CoursesService();
        this.courses = service.getCourses();
    }
```
better use DI
```
    constructor(service: CoursesService) {
        this.courses = service.getCourses();
    }
```
The important thing is, if you want to use DI you have to register your service in `app.module.ts` within the providers array. So it will be available in the whole project (Singelton pattern)

#### Its possible to create a service with angular cli
`$ ng g s service` (s = service)