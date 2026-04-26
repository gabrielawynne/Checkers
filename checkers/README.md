# Multiplayer Checkers

A full-stack multiplayer checkers game with a Java backend and browser-based frontend. Players connect over WebSockets for real-time gameplay. Supports human vs human, human vs bot, and includes a matchmaking system that pairs players together automatically.

## Features

- Real-time multiplayer via WebSockets
- Two bot difficulty levels (BotI and BotII)
- Player authentication — accounts and match history stored in SQLite
- Web frontend served directly from the Java HTTP server (no separate web server needed)

## Stack

- Java 17, Maven
- [java-websocket](https://github.com/TooTallNate/Java-WebSocket) for WebSocket handling
- Gson for JSON serialization between client and server
- SQLite (`players.db`) for persistence
- JUnit 4 + Mockito for tests

## Build & Run

You need Java 17 and Maven installed.

```bash
mvn package
java -jar target/checkers-1.0-SNAPSHOT.jar
```

Then open your browser and go to `http://localhost:9502`. The server handles both HTTP (for serving the frontend) and WebSocket connections on the same port.

The SQLite database (`players.db`) is created automatically on first run in the project root.

## Project Structure

```
src/
  main/java/cse3310/
    App.java              # entry point
    HttpServer.java       # serves the web frontend
    GameManager/          # game state and session management
    GamePlay/             # board, pieces, move logic
    Bot/                  # BotI and BotII implementations
    DB/                   # SQLite connection, user auth, password manager
    PairUp/               # matchmaking
    PageManager/          # handles client events
    GameTermination/      # end-of-game logic
  main/resources/         # frontend HTML, JS, CSS
```
