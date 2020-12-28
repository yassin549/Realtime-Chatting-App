# Anonymous Real-time Chat  

## 🚀 Introduction  

This **Anonymous Chat App** demonstrates how to create a real-time chat application using **Node.js**, **Express**, **Socket.IO**, and **MongoDB**.  

By exploring this application, you'll:  
- Gain a solid understanding of **Socket.IO** for real-time communication.  
- Learn how to implement features like **"user is typing" notifications**.  
- See a practical integration of a simple **MongoDB database** for storing chat messages.  

Below is a snapshot showcasing the app's user interface and functionality:  

![Chat Screen Shot](https://github.com/rexeze/anonymouse-realtime-chat-app/blob/master/screenshots/chatscreenshot.gif)  

---

## 🛠 Features  

- Real-time anonymous chat functionality.  
- Notifications when users are typing.  
- Automatic broadcasting of chat messages to all connected users.  
- Frontend and backend communication using **Socket.IO**.  
- Simple and lightweight UI with dynamic message handling.  

---

## 🔥 Code Overview  

### Backend Code Sample  

This code demonstrates how to integrate **Socket.IO** and handle real-time events.  

```javascript  
const socket = io(http);  
const Chat = require("./models/Chat");  
const connect = require("./dbconnect");  

// Setup socket event listeners  
socket.on("connection", (socket) => {  
  console.log("User connected");  

  socket.on("disconnect", () => {  
    console.log("User disconnected");  
  });  

  // Handle "user is typing" notifications  
  socket.on("typing", (data) => {  
    socket.broadcast.emit("notifyTyping", {  
      user: data.user,  
      message: data.message,  
    });  
  });  
});  
```  

### Frontend Code Sample  

This code handles user input and renders chat messages dynamically on the client side.  

```javascript  
(function () {  
  $("form").submit((e) => {  
    e.preventDefault(); // Prevent page reload  
    socket.emit("chat message", $("#message").val());  

    const li = document.createElement("li");  
    const span = document.createElement("span");  
    messages.appendChild(li).append($("#message").val());  
    messages.appendChild(span).append("by Anonymous: just now");  
    $("#message").val("");  

    return false;  
  });  

  // Listen for received messages  
  socket.on("received", (data) => {  
    const li = document.createElement("li");  
    const span = document.createElement("span");  
    messages.appendChild(li).append(data.message);  
    messages.appendChild(span).append("by anonymous: just now");  
  });  
})();  
```  

---

## 📦 Installation  

### Prerequisites  

1. **Node.js** and **npm** installed on your system.  
2. **MongoDB** installed and running locally.  

### Steps  

1. Clone this repository:  
   ```bash  
   git clone https://github.com/yassin549/Realtime-Chatting-App  
   ```  

2. Navigate to the project directory:  
   ```bash  
   cd Realtime-Chatting-App 
   ```  

3. Install dependencies:  
   ```bash  
   npm install  
   ```  

4. Start the app:  
   ```bash  
   npm start  
   ```  

5. Open your browser and visit:  
   ```
   http://localhost:5000  
   ```  

---

## 📝 Notes  

- Ensure **MongoDB** is installed and running for the app to function correctly.  
- The app is configured to run on port **5000** by default. You can change the port in the server configuration if needed.  

---

## 🌟 Features to Explore  

1. Try typing in the chat box to see real-time **"user is typing" notifications**.  
2. Send messages anonymously and watch them broadcasted to all connected users.  
3. Modify the code to add new features like:  
   - Chat room segregation.  
   - User authentication.  
   - Persisting chat history.  

---

## 📧 Contact  

If you have questions or need help, feel free to reach out:  
- **Email**: officialyassinkhoualdi@gmail.com 


---

## 📜 License  

This project is licensed under the **MIT License**. Feel free to use it for your projects.  

---
