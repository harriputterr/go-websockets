# 🧠 Real-Time Go Chat Server

Welcome to a real-time WebSocket-based chat server built with **Go (Golang)** and **vanilla HTML/JS frontend**! This project demonstrates how to build a scalable, event-driven backend using Go's concurrency model and Gorilla WebSocket library.

---

## 🚀 Features

- ✅ Real-time messaging via WebSockets
- 🔁 Event-based architecture with typed event handling
- 👥 Supports multiple clients with connection management
- 🔐 Clean shutdown via ping/pong heartbeat
- 📄 Simple HTML + JS frontend (no frameworks)

---

## 🏗️ Project Structure

```
├── main.go         # Entry point, HTTP server setup
├── manager.go      # Manages connected clients and event routing
├── client.go       # Represents each WebSocket client (read/write)
├── event.go        # Defines event types and payload structure
├── index.html      # Frontend UI and client WebSocket code
└── README.md       # You're here!
```

---

## ⚙️ How It Works

1. User connects to the WebSocket server at `/ws`
2. Server upgrades the connection and registers the client
3. Messages are sent from the frontend as typed events:
   ```json
   { "type": "send_message", "payload": "Hello from client!" }
   ```
4. The server routes events based on their type (e.g. `send_message`)
5. Messages are (or will be) broadcasted to other connected clients
6. Ping/pong messages ensure dead clients are disconnected

---

## 📦 Running the Project

### 1. Install dependencies
```bash
go get github.com/gorilla/websocket
```

### 2. Run the server
```bash
go run main.go
```

### 3. Open the app
Navigate to: [http://localhost:8080](http://localhost:8080)

---

## 📡 WebSocket Heartbeat Logic

To prevent zombie clients:
- A ping is sent every 9s
- A pong must be received within 10s
- If not, the connection is closed automatically

---

## 🧪 Try It Out

1. Open multiple tabs
2. Type messages in the chat
3. (Planned) See real-time broadcast across tabs

---

## 🛣️ Roadmap

- [x] Base WebSocket server with event routing
- [x] Client manager with safe concurrency
- [x] Frontend WebSocket integration
- [x] Ping/pong heartbeat
- [ ] Broadcast messages to all clients
- [ ] Support chatrooms / channels
- [ ] Store chat history

---

## 🧠 Learnings

This project teaches:
- Go's `select` and channel-based signaling
- Safe concurrency using goroutines
- Event-driven backend design
- Real-time frontend/backend communication

---

## 👨‍💻 Author
Built by Harsingh Sekhon, 2025

---

## 📜 License
MIT License. Use freely, contribute boldly!

