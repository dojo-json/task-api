
### Up and Running in Minutes

#### Clone the project
` git clone https://github.com/dojo-json/task-api && cd task-api`

#### Install Dependencies 
npm: `npm i`    
or    
yarn: `yarn install`

#### Start The Server
`nodemon` 

### Consuming the Task Resource 

In your `TaskService`, you may set a static base:

```typescript 

import { Injectable } from '@angular/core';
import { Http } from '@angular/http';

import 'rxjs/add/operator/toPromise';
import 'rxjs/add/operator/map';

import { Task } from './task';

@Injectable() 
export class TaskService {
  public static base = 'http://localhost:8000/api/tasks';

  constructor(private _http: Http) {} 

  retrieveTasks(): Promise<Task[]> {
    return this._http.get(TaskService.base)
      .map(response => response.json())
      .toPromise();
  }

  retrieveTask(id: string): Promise<Task> {
    return this._http.get(`${ TaskService.base }/${ id }`)
    .map(response => response.json())
    .toPromise();
  }
  // the rest of your CRUD functionality ...
}

```
