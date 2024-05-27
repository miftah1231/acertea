# Simple Chat Application with Node.js

## Description
This project is a simple chat application built using Node.js and Socket.io. It allows users to send real-time messages to each other in a chat room.

## Key Features
- Real-time messaging with Socket.io
- Simple and responsive user interface
- Notifications when users join and leave the chat room

## Prerequisites
Make sure you have Node.js and npm installed on your computer. You can download them from [nodejs.org](https://nodejs.org/).

## Installation
Follow these steps to install and run the chat application:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/miftah1231/acertea.git

2. **Add cd**
    ```bash
    cd acertea
    npm install
3. **Write the code (Create name file server.js)**
   
const express = require('express');
const http = require('http');
const socketIo = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIo(server);

const PORT = process.env.PORT || 3000;

app.use(express.static('public'));

io.on('connection', (socket) => {
  console.log('New user connected');

  socket.on('disconnect', () => {
    console.log('User disconnected');
  });

  socket.on('chatMessage', (msg) => {
    io.emit('chatMessage', msg);
  });
});

server.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

4. **Create a directory named public inside your project directory and add a file named index.html**
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chat App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="chat-container">
    <div id="chat-box"></div>
    <input id="chat-input" type="text" placeholder="Type a message...">
    <button id="send-btn">Send</button>
  </div>

  <script src="/socket.io/socket.io.js"></script>
  <script>
    const socket = io();

    document.getElementById('send-btn').addEventListener('click', () => {
      const msg = document.getElementById('chat-input').value;
      socket.emit('chatMessage', msg);
      document.getElementById('chat-input').value = '';
    });

    socket.on('chatMessage', (msg) => {
      const chatBox = document.getElementById('chat-box');
      const msgElement = document.createElement('div');
      msgElement.textContent = msg;
      chatBox.appendChild(msgElement);
    });
  </script>
</body>
</html>


5. **Running the Application**
   To run the application, use the following command in your terminal:
    ```bash
   node server.js
    
Open your browser and navigate to http://localhost:3000 to access the chat application.

**Contributing**
We welcome contributions from everyone. Here’s how you can contribute:

Fork this repository.
1. Create your feature branch (git checkout -b your-feature).
2. Commit your changes (git commit -m 'Add some feature').
3. Push to the branch (git push origin your-feature).
4. Create a new Pull Request.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Contact
If you have any questions or feedback, feel free to contact us at:

Email: miftahurrizki174@gmail.com
Twitter: @miftahur
GitHub Issues: [Issues](https://github.com/miftah1231/acertea.git)
Thank you for using the Simple Chat Application! We hope this project is helpful to you.

You can copy and paste this template into the `README.md` file in your GitHub repository. Be sure to customize the sections with the appropriate details for your project, such as the project name, installation instructions, and contact information. If you need any additional information or further customization, let me know!





