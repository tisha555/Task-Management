# **Realtime Todo Task Management App using NestJS and Angular**  

This project is a **real-time task management system** designed to provide seamless task tracking and organization. It is built using **NestJS for the backend** and **Angular for the frontend**, leveraging **WebSockets** for real-time updates and **JWT authentication** for secure access. The app also features **drag-and-drop task organization**, ensuring a smooth and interactive user experience.

---

## **Technology Stack**  

### **Backend (NestJS)**  
- **NestJS (with TypeScript)** – A powerful Node.js framework that follows the modular architecture of Angular.  
- **PostgreSQL (via TypeORM)** – A relational database for storing user accounts and tasks.  
- **WebSockets (Socket.io)** – Enables real-time communication for instant updates across clients.  
- **JWT Authentication** – Used to secure API endpoints and manage user sessions.  
- **Docker** – Containerizes the backend for easy deployment and scalability.  
- **Swagger** – Provides API documentation for better development and testing.  
- **Validation (class-validator & class-transformer)** – Ensures request data integrity.  
- **REST API & GraphQL (optional)** – Supports both traditional API calls and GraphQL queries.  

### **Frontend (Angular)**  
- **Angular (TypeScript)** – A robust framework for building dynamic web applications.  
- **Angular Material** – Provides UI components like modals, forms, and buttons.  
- **RxJS** – Handles asynchronous operations efficiently.  
- **Drag-and-Drop (Angular CDK)** – Allows users to rearrange tasks with ease.  
- **WebSockets (Socket.io-client)** – Enables real-time updates from the backend.  
- **JWT-based AuthGuard** – Protects private routes from unauthorized users.  
- **State Management (NGXS or Akita)** – Manages global state effectively.  
- **Tailwind CSS** – Simplifies UI styling with utility-first classes.  

### **DevOps & Deployment**  
- **Docker & Docker Compose** – Ensures easy local setup and containerized deployment.  
- **CI/CD (GitHub Actions)** – Automates testing and deployment.  
- **Cloud Deployment (Render, Fly.io, Vercel, or DigitalOcean)** – Deploys the app for public access.  
- **Nginx or Traefik (Reverse Proxy)** – Manages API and frontend routing.  
- **PostgreSQL Database (Hosted on Railway or Supabase)** – Provides scalable data storage.  

---

## **Features & Functionality**  

### **1. User Authentication & Authorization**  
- **Signup/Login with JWT Authentication**  
- **Role-based access control** (Admin/User)  
- **Session persistence using HTTP-only cookies or local storage**  
- **Password hashing with bcrypt for security**  

### **2. Real-time Task Management**  
- **Create, Edit, Delete, and Mark tasks as complete**  
- **Drag-and-drop tasks into different categories**  
- **Real-time synchronization of tasks across multiple devices using WebSockets**  
- **Task filtering by status (Pending, In Progress, Completed)**  

### **3. WebSocket-based Real-time Updates**  
- **Users see task updates instantly without refreshing the page**  
- **Broadcast changes to all connected clients**  
- **Efficient state management to avoid unnecessary re-renders**  

### **4. Task Categories & Prioritization**  
- **Categorize tasks based on priority (High, Medium, Low)**  
- **Use color-coded tags for better organization**  
- **Option to set due dates and reminders**  

### **5. Drag-and-Drop Functionality**  
- **Reorder tasks using Angular CDK drag-and-drop module**  
- **Preserve new order in the database**  
- **Improve user experience with animations and smooth transitions**  

### **6. Secure API with Rate Limiting**  
- **Prevents brute-force attacks**  
- **Limits the number of requests per user/session**  
- **Uses NestJS's built-in throttling package**  

### **7. Offline Support & PWA Integration (Optional)**  
- **Enables working offline with cached tasks**  
- **Syncs changes when back online**  
- **Push notifications for important updates**  

### **8. Dark Mode & Custom Themes**  
- **Toggle between light and dark mode**  
- **Customizable UI using Tailwind’s theming system**  
- **Improved accessibility with high contrast options**  

### **9. Slack/Discord Bot Integration (Future Feature)**  
- **Automate reminders via Slack/Discord notifications**  
- **Fetch task summaries directly from a chat command**  
- **Integrate AI-powered task recommendations**  

---

## **System Architecture**  
### **Backend (NestJS)**  
- **Authentication Module**  
- **Tasks Module**  
- **WebSocket Gateway**  
- **Database Module**  
- **Config Module (for environment variables)**  

### **Frontend (Angular)**  
- **AuthService** (Handles JWT authentication)  
- **TaskService** (Manages task CRUD operations)  
- **WebSocketService** (Listens for real-time task updates)  
- **State Management (NGXS/Akita)**  
- **UI Components (Angular Material)**  

---

## **Database Schema (PostgreSQL)**  
```sql  
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE tasks (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    status VARCHAR(20) CHECK (status IN ('Pending', 'In Progress', 'Completed')),
    priority VARCHAR(10) CHECK (priority IN ('High', 'Medium', 'Low')),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

---

## **Deployment Workflow**  
1. **Develop locally using Docker Compose**  
2. **Push changes to GitHub (CI/CD triggers build)**  
3. **Run automated tests for API and UI**  
4. **Deploy backend to Fly.io / Render**  
5. **Deploy frontend to Vercel**  
6. **Database hosted on Railway / Supabase**  
7. **Monitor logs using Prometheus & Grafana**  

---

## **Project Roadmap**  
### **Phase 1: Core Features (MVP)**  
✅ Setup NestJS backend with authentication  
✅ Implement task CRUD operations  
✅ Integrate WebSockets for real-time updates  
✅ Build Angular frontend with Material UI  

### **Phase 2: Enhancements**  
✅ Add drag-and-drop functionality  
✅ Optimize state management with NGXS  
✅ Implement dark mode and themes  

### **Phase 3: Advanced Features**  
⏳ PWA Support for offline usage  
⏳ AI-powered task recommendations  
⏳ Slack/Discord bot for notifications  

---

## **Conclusion**  
This **Realtime Todo Task Management App** combines **NestJS, Angular, WebSockets, and PostgreSQL** to provide a seamless and interactive user experience. 🚀

