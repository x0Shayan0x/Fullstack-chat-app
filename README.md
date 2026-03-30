# 💬 FullStack Chat App

A real-time full-stack chat application built with the **MERN stack** and **Socket.io**. Features one-on-one messaging, live online/offline presence, image sharing, customizable themes, and persistent sessions — all wrapped in a sleek, responsive UI.

🔗 **[Live Demo](https://fullstack-chat-app-6uba.onrender.com/)**

---

## ✨ Features

- **Real-time messaging** — instant bidirectional communication via WebSockets
- **One-on-one DMs** — private conversations between users
- **Online / Offline status** — see who's active in real time
- **Image & file sharing** — send images directly in chat
- **Customizable themes** — personalize the UI to your preference
- **JWT authentication + refresh tokens** — secure, stateless auth with automatic token renewal
- **Persistent sessions** — stay logged in across browser restarts, no repeated sign-ins
- **Password hashing** — all passwords stored securely via bcrypt
- **Sleek, responsive UI** — clean design that works across devices

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, Vite |
| Styling | Tailwind CSS, DaisyUI |
| Real-time | Socket.io |
| Backend | Node.js, Express |
| Database | MongoDB Atlas |
| ODM | Mongoose |
| Auth | JWT (access + refresh tokens), bcrypt |
| File Uploads | Cloudinary |
| State Management | Zustand |

---

## 🔐 Authentication Flow

1. User signs up — password is hashed with **bcrypt** before storage
2. On login, server issues a short-lived **access token** (15m) and a long-lived **refresh token** (7d)
3. Refresh token is stored in an **httpOnly cookie**, inaccessible to JavaScript, protecting against XSS
4. Access token is stored in memory and automatically renewed via the refresh endpoint
5. On app load, session is restored silently if a valid refresh token cookie exists — no re-login required

---

## 🌐 Real-time Architecture

Socket.io runs alongside the Express server on the same port. On login, the client establishes a persistent WebSocket connection. The server maintains a map of `userId → socketId` to:

- Emit messages instantly to the correct recipient
- Broadcast online/offline presence updates to all connected clients

---
