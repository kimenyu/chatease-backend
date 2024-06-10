# ChatEase

ChatEase is a real-time chat application built using Node.js, Express, MongoDB, and Socket.io. This application allows users to register, login, send and receive messages, and set avatar images.

## Features

- **User Registration and Login**
- **Real-time Messaging**: Enabled by Socket.io
- **Persistent Message Storage**: Using MongoDB
- **User Avatar Management**
- **RESTful API**: For user and message operations

## Technologies

- **Back-End**: JavaScript (ES6), Node.js, Express.js
- **Database**: MongoDB (NoSQL database for storing user and message data)
- **Real-Time Communication**: Socket.io
- **Other Libraries**: bcrypt (for password hashing), dotenv (for environment variables), cors (for handling cross-origin requests)

## Setup and Installation

### Prerequisites

- Node.js
- MongoDB
- npm or yarn

### Steps

1. **Clone the repository:**

    ```bash
    git clone https://github.com/yourusername/chatease.git
    cd chatease
    ```

2. **Install dependencies:**

    ```bash
    npm install
    ```

3. **Create a `.env` file in the root directory and add your MongoDB connection string and server port:**

    ```plaintext
    MONGO_URL=your_mongodb_connection_string
    PORT=your_server_port
    ```

4. **Start the server:**

    ```bash
    npm start
    ```

## API Endpoints

### Auth Routes

- **POST /api/auth/login**: User login
  - Request body: `{ "username": "user", "password": "pass" }`
  - Response: User object or error message

- **POST /api/auth/register**: User registration
  - Request body: `{ "username": "user", "email": "user@example.com", "password": "pass" }`
  - Response: User object or error message

- **GET /api/auth/logout/:id**: User logout
  - Params: `id` - User ID
  - Response: Success or error message

### User Routes

- **GET /api/auth/allusers/:id**: Get all users except the one with the given ID
  - Params: `id` - User ID
  - Response: Array of user objects

- **POST /api/auth/setavatar/:id**: Set avatar image
  - Params: `id` - User ID
  - Request body: `{ "image": "base64_encoded_image" }`
  - Response: Avatar image data or error message

### Message Routes

- **POST /api/messages/addmsg/**: Add a new message
  - Request body: `{ "from": "userId", "to": "userId", "message": "Hello!" }`
  - Response: Success or error message

- **POST /api/messages/getmsg/**: Get messages between two users
  - Request body: `{ "from": "userId", "to": "userId" }`
  - Response: Array of messages

## Project Structure

```plaintext
.
├── controllers
│   ├── messageController.js
│   └── userController.js
├── models
│   ├── messageModel.js
│   └── userModel.js
├── routes
│   ├── auth.js
│   └── messages.js
├── .env
├── app.js
├── package.json
└── README.md
