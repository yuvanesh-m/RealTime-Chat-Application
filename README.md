# Real-Time Chat Application

A real-time web-based chat application built using **Java, Spring Boot, WebSocket, STOMP, SockJS, and Bootstrap**.

## 🚀 Live Deployment

**[Open Chat Application](http://3.26.238.10:8080/chat)**

## ✨ Features

- Real-time messaging using WebSocket
- STOMP messaging protocol
- SockJS fallback support
- Multiple users in the same chat room
- Username-based message display
- Consistent username colors
- Responsive UI using Bootstrap
- Dockerized deployment
- AWS EC2 deployment

## 🛠️ Technologies Used

### Backend

- Java 21
- Spring Boot
- Spring WebSocket
- STOMP
- SockJS

### Frontend

- HTML
- CSS
- JavaScript
- Bootstrap

### Deployment

- Docker
- AWS EC2
- GitHub

## 🏗️ Architecture

```text
User Browser
     |
     v
SockJS + STOMP
     |
     v
Spring Boot Application
     |
     v
Chat Controller
     |
     v
@MessageMapping("/sendMessage")
     |
     v
@SendTo("/topic/message")
     |
     v
All Connected Clients

## 🔄 Message Flow

1. User opens the chat application.
2. Browser establishes a WebSocket connection through SockJS.
3. Client subscribes to `/topic/message`.
4. User sends a message to `/app/sendMessage`.
5. Spring Boot receives the message through `@MessageMapping`.
6. The message is broadcast to `/topic/message`.
7. All connected users receive the message in real time.

## 🔌 WebSocket Destinations

| Destination | Purpose |
|---|---|
| `/chat` | WebSocket connection endpoint |
| `/app` | Application destination prefix |
| `/topic` | Message broker destination |
| `/app/sendMessage` | Send chat messages |
| `/topic/message` | Broadcast messages |

## 📁 Project Structure

```text
RealTime-Chat-Application/
│
├── src/
│   └── main/
│       ├── java/
│       └── resources/
│
├── Dockerfile
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md

## ▶️ How to Run the Application

### 1. Clone the Repository

```bash
git clone https://github.com/yuvanesh-m/RealTime-Chat-Application.git
cd RealTime-Chat-Application
```

### 2. Build the Application

```bash
chmod +x mvnw
./mvnw clean package -DskipTests
```

### 3. Run the Application Locally

```bash
./mvnw spring-boot:run
```

Open the application in your browser:

http://localhost:8080/chat

### 4. Run Using Docker

Build the Docker image:

```bash
docker build -t chat-app:latest .
```

Run the Docker container:

```bash
docker run -d --name chat-app --restart unless-stopped -p 8080:8080 chat-app:latest
```

Check the running container:

```bash
docker ps
```

View application logs:

```bash
docker logs -f chat-app
```

Open the application:

http://localhost:8080/chat

### 5. Deploy on AWS EC2

Connect to your AWS EC2 instance and clone the repository:

```bash
git clone https://github.com/yuvanesh-m/RealTime-Chat-Application.git
cd RealTime-Chat-Application
```

Build the application:

```bash
chmod +x mvnw
./mvnw clean package -DskipTests
```

Build the Docker image:

```bash
docker build -t chat-app:latest .
```

Run the Docker container:

```bash
docker run -d --name chat-app --restart unless-stopped -p 8080:8080 chat-app:latest
```

Check the container:

```bash
docker ps
```

View application logs:

```bash
docker logs -f chat-app
```

### 6. Configure AWS Security Group

Add an inbound rule to the EC2 Security Group:

| Type | Port | Source |
|---|---:|---|
| Custom TCP | 8080 | 0.0.0.0/0 |

### 7. Access the Deployed Application

The application is deployed on AWS EC2 and can be accessed at:

**http://3.26.238.10:8080/chat**

### 8. Docker Container Management

Stop the container:

```bash
docker stop chat-app
```

Start the container:

```bash
docker start chat-app
```

Restart the container:

```bash
docker restart chat-app
```

Check container status:

```bash
docker ps
```

View container logs:

```bash
docker logs -f chat-app
```

Remove the container:

```bash
docker rm -f chat-app
```
