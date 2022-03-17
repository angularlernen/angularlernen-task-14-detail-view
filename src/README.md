Detail View - Routing with Parameters
=====================================

### Introduction

Let's create the Detail view for a selected MicroEvent.

### Task

1. Create a new component `event-detail` as part of your `events` module: `ng g c events/event-detail`.

2. Add a new routing configuration to this new component for the path: `events/:id`.

3. Add `findById(id: number)` methods to the `EventResource` and `ProfileResource` injectables.

4. Add a `findById(id: number): Observable<MicroEvent>` method to the `MicroEventService`.

5. Use the `ActivatedRoute` injectable from `@angular/router` to access the URL Parameters.

6. Use the `findById` method on the injected `MicroEventService` to load the `MicroEvent`.

7. Render some details of the `MicroEvent`.

### HOWTOs

#### app-routing.module.ts

```ts
{
    path: 'events/:id',
    component: EventDetailComponent
}, // ...
```

### event.resource.ts

`http://localhost:3000/events/1`

### profile.resource.ts

`http://localhost:3000/profiles/1`

### micro-event.service.ts - findById

We implemented this for you :-)

### event-detail.component.ts

```ts
import { ActivatedRoute } from "@angular/router";

import { MicroEvent } from '../../shared/domain/micro-event';
import { MicroEventService } from '../../shared/domain/micro-event.service';
```

```ts
event: MicroEvent;

  constructor(private _route: ActivatedRoute, 
              private _microEventService: MicroEventService) { }
```

```ts
ngOnInit() {
    this._route.params.subscribe((params: { id: number }) => {
      // ....
    });
  }
```

The goal here is to set this member which is bound in the template: `event: MicroEvent`.
