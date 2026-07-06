# Real-Time Code Editor

A collaborative real-time code editor built with **React, Node.js, Express, Socket.IO, and CodeMirror**. The application allows multiple users to join a shared room, edit code simultaneously, and see updates in real time through WebSocket-based synchronization.

## Features

* Create and join collaborative coding rooms using a unique Room ID
* Real-time code synchronization across all users in the same room
* Multi-user collaboration with a live connected-users panel
* Shared code state for new users joining an existing room
* Copy Room ID functionality for easy sharing
* Toast notifications for user join/leave events and room actions
* Code editor interface powered by **CodeMirror**

## Tech Stack

* **Frontend:** React, React Router
* **Backend:** Node.js, Express
* **Real-Time Communication:** Socket.IO
* **Editor:** CodeMirror
* **Utilities:** UUID, React Hot Toast, React Avatar

## Project Structure

```bash
realtime-code-editor/
├── public/                     # Static assets
├── src/
│   ├── components/            # Reusable UI components
│   │   ├── Client.js          # Connected user card
│   │   └── Editor.js          # CodeMirror editor with socket sync
│   │
│   ├── pages/
│   │   ├── Home.js            # Room creation / join page
│   │   └── EditorPage.js      # Collaborative editor workspace
│   │
│   ├── Actions.js             # Socket event constants
│   ├── socket.js              # Socket.IO client initialization
│   ├── App.js                 # App routes
│   └── index.js
│
├── server.js                  # Express + Socket.IO backend
├── package.json
└── README.md
```

## How It Works

1. A user creates a new room or joins an existing room using a Room ID.
2. On joining, the client establishes a Socket.IO connection with the server.
3. The server adds the user to the room and broadcasts the updated participant list.
4. Any code changes made by a user are emitted to the room and reflected in real time for all connected users.
5. When a new user joins, the current editor state is synchronized so everyone sees the same code.

## Installation and Setup

### Prerequisites

* Node.js
* npm

### Run Locally

```bash
git clone <your-repo-link>
cd realtime-code-editor
npm install
```

### Start the frontend

```bash
npm run start:front
```

### Start the backend

```bash
npm run server:dev
```

The frontend runs on `http://localhost:3000` and the backend runs on `http://localhost:5000`.

> Make sure the frontend socket connection points to the backend URL through `REACT_APP_BACKEND_URL`.

## Socket Events

The application uses the following Socket.IO events for collaboration:

* `JOIN` – user joins a room
* `JOINED` – broadcast updated room participants
* `CODE_CHANGE` – send code updates to other users in the room
* `SYNC_CODE` – sync current editor state with a newly joined user
* `DISCONNECTED` – notify users when someone leaves the room

## Future Improvements

* Add support for multiple programming languages
* Integrate code compilation/execution
* Add in-room chat and voice collaboration
* Persist room sessions and editor history
* Add authentication and private rooms

