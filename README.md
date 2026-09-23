Real-Time Chat Application

A real-time web-based chat application built using Java, Spring Boot,
WebSocket, STOMP, SockJS, and Bootstrap. The application allows
multiple users to connect to a shared chat room and exchange messages in
real time without refreshing the page.

🚀 Live Deployment

http://3.26.238.10:8080/chat

The application is currently deployed on AWS EC2 using a public IP.
The URL may become unavailable if the EC2 instance is stopped or if
its public IP changes.

✨ Features

Real-time messaging using WebSocket

STOMP messaging protocol

SockJS fallback support

Multiple users in the same chat room

Username-based message display

Consistent username colors

Bootstrap-based responsive UI

Spring Boot backend

Dockerized deployment

AWS EC2 deployment

🛠️ Technologies Used

Backend

Java 21

Spring Boot

Spring WebSocket

STOMP

SockJS

Frontend

HTML

CSS

JavaScript

Bootstrap

Deployment

Docker

AWS EC2

GitHub

🏗️ Architecture

User Browser
     |
     | SockJS / STOMP
     v
Spring Boot Application
     |
     | @MessageMapping
     v
Chat Controller
     |
     | @SendTo
     v
STOMP Topic
     |
     v
All Connected Clients

🔄 Message Flow

The user opens the chat application.

The browser establishes a connection with the Spring Boot WebSocket
endpoint /chat.

The client subscribes to /topic/message.

When a user sends a message, the client sends it to
/app/sendMessage.

Spring Boot receives the message through
@MessageMapping("/sendMessage").

The message is broadcast to /topic/message.

All subscribed clients receive and display the message instantly.

🔌 WebSocket Destinations

Purpose              Destination

WebSocket endpoint   /chat
Application prefix   /app
Broker prefix        /topic
Send message         /app/sendMessage
Subscribe            /topic/message

📁 Project Structure

RealTime-Chat-Application/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── ...
│   │   └── resources/
│   │       ├── static/
│   │       ├── templates/
│   │       └── application.properties
│   └── test/
├── Dockerfile
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md

💻 Run Locally

Prerequisites

Java 21

Maven

Git

Docker (optional)

Clone the Repository

git clone https://github.com/yuvanesh-m/RealTime-Chat-Application.git
cd RealTime-Chat-Application

Build and Run

./mvnw clean package
./mvnw spring-boot:run

If required:

chmod +x mvnw

Open:

http://localhost:8080/chat

🐳 Docker

The application uses Eclipse Temurin Java 21 as the runtime image.

Build the JAR

./mvnw clean package -DskipTests

Build the Docker Image

docker build -t chat-app:latest .

Run the Container

docker run -d   --name chat-app   --restart unless-stopped   -p 8080:8080   chat-app:latest

Check the container:

docker ps

View logs:

docker logs -f chat-app

☁️ AWS EC2 Deployment

The application is deployed on an AWS EC2 instance using Docker.

Local Development
       |
       v
     GitHub
       |
       v
    AWS EC2
       |
       v
 Docker Image
       |
       v
 Docker Container
       |
       v
   Port 8080
       |
       v
 Public Internet

Deployment Steps

git clone https://github.com/yuvanesh-m/RealTime-Chat-Application.git
cd RealTime-Chat-Application

./mvnw clean package -DskipTests

docker build -t chat-app:latest .

docker run -d   --name chat-app   --restart unless-stopped   -p 8080:8080   chat-app:latest

The EC2 security group must allow inbound TCP traffic on port 8080.

🔐 WebSocket Configuration

For the deployed application, the WebSocket endpoint can be configured
as:

registry.addEndpoint("/chat")
        .setAllowedOriginPatterns("*")
        .withSockJS();

For production, restrict allowed origins to the actual application
domain instead of using *.

🧪 Testing

Open the deployed application in multiple browser tabs:

http://3.26.238.10:8080/chat

Use different usernames and send messages. Messages should be broadcast
to all connected clients in real time.

🔧 Useful Docker Commands

docker ps
docker ps -a
docker logs chat-app
docker logs -f chat-app
docker stop chat-app
docker start chat-app
docker rm chat-app

🔮 Future Enhancements

User authentication and authorization

Private one-to-one messaging

Persistent chat history

Database integration

Online/offline status

Typing indicators

Message timestamps

Read receipts

HTTPS/WSS support

Custom domain

Nginx reverse proxy

👨‍💻 Author

Yuvanesh M

Java Backend Developer

GitHub: https://github.com/yuvanesh-m
