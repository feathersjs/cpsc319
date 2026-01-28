---
theme: ./theme
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## CPSC 319 kickoff
transition: slide-left
title: CPSC 319 kickoff
background: /images/launch-bridge.svg
dim: true
---

# CPSC 319 Feathers kickoff

---
class: text-center
layout: cover
---

# Hi, I'm David

### I make open source things at
### [feathers.dev](https://feathers.dev) and [feathersjs.com](https://feathersjs.com)

<img src="/images/spacebird.svg" class="w-50 mx-a mt-4" alt="Space bird!" />

---
layout: cover
---

# Today I'd like to talk about

- A short history of the Internet 🌍
- Design patterns 
- HTTP and REST
- Feathers 🪶

---

<img alt="Arpanet chart" style="height: 100%; margin: 0 auto;" src="images/arpanet.png" />

---
layout: cover
background: /images/att-jack.jpg
---

---

<img alt="WWW chart" style="height: 100%; margin: 0 auto;" src="images/www.gif" />

---

```html
GET /thesis HTTP/1.1
Host: daffl.github.io
User-Agent: Mozilla/5.0
Accept: text/html,application/json;q=0.8
Accept-Language: en,de;q=0.9

HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 389
Date: Wed, 27 Mar 2019 23:14:25 GMT
Connection: keep-alive

<!DOCTYPE html>
<html>
  <body>
  </body>
</html>
```

---
layout: cover
class: text-center
---

# REST

**Re**presentational **S**tate **T**ransfer is an architectural style
that defines a set of constraints for creating web APIs.
The HTTP _protocol_ is one implementation of this architecture. [[Fielding PHD thesis](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)]

---
layout: cover
---

# REST Constraints

- __Client__  (Requesting and displaying) - __Server__ (Data storage and application logic)
- __Statelessness:__ Client sends all information with each request
- __Caching:__ Non-modifying requests can be cached
- __Layered System:__ Simplify by layering responsibilities
- __Resources__ and __Uniform Interface__

---

# REST Resources and Operations

A resource can be anything that is uniquely addressable.

- __GET:__ Read a single or a list of resources
- __POST:__ Create a new resource
- __PUT:__ Replaces resource(s) with new data
- __PATCH:__ Merges the resource(s) with new data
- __DELETE:__ Delete the resource(s) at location

---
layout: cover
---

# Service Layer

Defines an application’s boundary with a layer of services that
establishes a set of available operations and coordinates the application’s
response in each operation. [[P of EAA](https://martinfowler.com/eaaCatalog/serviceLayer.html)]

---

<img alt="Service layer" style="height: 100%; margin: 0 auto;" src="images/service-layer.png" />

---

```js
class ChatApplication {

  login (username, password) {},
    
  logout (user) {},
    
  joinChatRoom(roomId, user) {}
    
  sendMessage(message, roomId, user) {}

  sendPrivateMessage(message, receiverId, user) {}

}
```

---
layout: cover
---

# Why a Service Layer?

- _Separation of Concerns and Testability:_ Test the application logic separate from how it is being accessed
- _Self documenting:_ New developers can see what the application provides in the context of the programming language
- _Transport agnostic:_ Clients like a CLI, GUI or web framework can use the service layer directly

---

# REST Service Layer

| HTTP method | Service layer method |
| --- | --- |
| GET /messages      | messages.find() |
| GET /messages/1    | messages.get(1) |
| POST /messages     | messages.create(data) |
| PUT /messages/1    | messages.update(1, data) |
| PATCH /messages/1  | messages.patch(1, data) |
| DELETE /messages/1 | messages.remove(1) |

---

```ts
class MessageService {
  // Find a list of resources
  find(params) {}
  // Get a single resource by its id
  get(id, params) {}
  // Create a new resource
  create(data, params) {}
  // Replace an existing resource by its id with data
  update(id, data, params) {}
  // Merge new data into a resource
  patch(id, data, params) {}
  // Remove a resource by its id
  remove(id, params) {}
}
```

---

# Real-time

| HTTP method | Service layer method | Real-time event |
| --- | --- | --- |
| GET /messages      | messages.find() | - |
| GET /messages/1    | messages.get(1) | - |
| POST /messages     | messages.create(data) | `message created` |
| PUT /messages/1    | messages.update(1, data) | `message updated` |
| PATCH /messages/1  | messages.patch(1, data) | `message patched` |
| DELETE /users/1 | messages.remove(1) | `message removed` |

---

# Middleware

Workflows and cross-cutting concerns that can be added to services dynamically

- Validation
- Checking permissions
- Sending emails or other notifications
- Logging and profiling

---

```ts
import {
  sendEmailNotification, validateData, checkPermission
} from './middleware';

class MessageService {
  @hooks([
    sendEmailNotification,
    validateData
  ])
  create(data, params) {
    // Insert data e.g. into MongoDB
    return mongodb.collection('messages').insertOne(data);
  }

  @hooks([
    checkPermission
  ])
  remove(id, params) {}
}
```

---

```js
export async function checkPermission (context, next) {
  const { user } = context.params

  // e.g. { permissions: [ 'editor', 'admin' ] }
  if (!user.permissions.includes('editor')) {
    throw new Error('You are not allowed to do this!')
  }

  await next()
}
```

---
class: text-center
---

<img src="/images/logo-feathers-white.svg" class="mx-a mt-4 mb-12" alt="Feathers logo" />

# The universal web framework

---

<img alt="The truth behind open source" style="height: 100%; margin: 0 auto;" src="images/os-truth.jpg" />

---
layout: cover
background: /images/so-questions.jpg
---

---
layout: cover
---

# Questions for you

- How can open source be sustainable in the AI age?
- What does knowledge sharing look like?
- How can the benefits be distributed and made accessible to everybody?
