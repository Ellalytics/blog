---
layout: single
title:  "Floor System Design"
date:   2024-01-09 19:03:13 -0800
categories: Game
author_profile: true
---
Started as a fun idea from a [TV show](https://www.fox.com/the-floor/) quickly became a family favorite—and now it’s a hit at parties, school events, and team gatherings!


<a href="https://github.com/Ellalytics/TheFloorGame/" class="btn btn--primary">Learn more</a>

---

## **System Architecture**

```
+----------------+     +----------------+     +----------------+
|    Web UI      |     |  Game Logic   |     |  Question DB  |
| (HTML/JS/CSS)  |<--->|  (Flask App)  |<--->|  (SQLite)     |
+----------------+     +----------------+     +----------------+
        ^                      ^
        |                      |
        v                      v
+----------------+     +----------------+
|  Player Client |     |  Admin Panel   |
+----------------+     +----------------+
```


---

## **Tech Stack**
- **Frontend:** HTML/CSS/JavaScript, Flask Template Engine, WebSocket 
- **Backend:** Python Flask, SQLite (for data storage),RESTful API



## **Core Features**

- **Game Management Module**<br>
Game state management<br>
Player turn control<br>
Timer management<br>
Score calculation<br>
- **Question Management Module**<br>
Question category management<br>
Random question selection <br>
Answer validation <br>
Image resource management<br>
- **User Interface Module**<br>
Main game interface<br>
Question display<br>
Timer display<br>
Score display<br>
Answer display<br>

## **Game Flow**

| Phase                  | Steps                                                                 |
|------------------------|-----------------------------------------------------------------------|
| Initialization         | Load question database, Set game parameters, Wait for player readiness|
| Gameplay               | Random question selection, Display question image, Start timer, Receive player answers, Validate answers, Update scores, Switch players |
| Game End               | Calculate final scores, Display results, Save game records            |


```
+----------------+     +----------------+     +----------------+
|    Web UI      |     |  Game Logic   |     |  Question DB  |
| (HTML/JS/CSS)  |<--->|  (Flask App)  |<--->|  (SQLite)     |
+----------------+     +----------------+     +----------------+
        ^                      ^
        |                      |
        v                      v
+----------------+     +----------------+
|  Player Client |     |  Admin Panel   |
+----------------+     +----------------+
```


## **Extensions ING**
* Multiplayer battle mode
* Achievement system
* Social features



---

