---
title: "Welcome to Jekyll!"
date: 2019-04-18 15:34:30 -0400
categories:
  - blog
tags:
  - Processes
  - Jekyll
  - update
---

In PlantUML:

- `->`: Arrow is used for delivery message
- `-->`: Dotted Arrow is used for return message

```plantuml
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response
@enduml
```

```plantuml!
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response
@enduml
```
