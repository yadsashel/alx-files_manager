# **0x04. Files Manager**

This repository hosts a robust file manager application built with **Node.js**, offering an intuitive way to upload, manage, and share files. The application leverages a combination of modern technologies, including **Express.js**, **MongoDB**, **Redis**, and **Bull**, to deliver efficient and scalable file management solutions.

---

## **Table of Contents**
- [Project Overview](#project-overview)
- [File Structure](#file-structure)
- [Requirements](#requirements)
- [Setup](#setup)
- [Usage](#usage)
- [Endpoints](#endpoints)
- [Testing](#testing)

---

## **Project Overview**

The **Files Manager Application** provides the following core functionalities:

1. **File Management**  
   - Upload, view, and organize files.
   - Publish and unpublish files.
   - Generate thumbnails for images.

2. **User Management**  
   - Register and authenticate users.
   - Send welcome emails to new users.

3. **Background Processing**  
   - Handle tasks like email notifications and thumbnail generation using **Bull Queues**.

4. **Caching**  
   - Utilize **Redis** for faster performance and improved efficiency.

5. **Storage**  
   - Store metadata and user information in **MongoDB**.

---

## **File Structure**

The repository is organized as follows:

```plaintext
project-root/
│
├── controllers/
│   ├── AppController.js          # Handles application-level requests.
│   ├── AuthController.js         # Manages user authentication.
│   ├── UsersController.js        # Handles user-related actions.
│   ├── FilesController.js        # Manages file-related operations.
│   └── ...
│
├── routes/
│   ├── index.js                  # API route definitions.
│   └── ...
│
├── tests/                        # Test cases for different components.
│   ├── dbClient.test.js
│   ├── redisClient.test.js
│   ├── status.test.js
│   ├── stats.test.js
│   ├── users.test.js
│   └── ...
│
├── utils/                        # Utility files for database and Redis.
│   ├── db.js
│   ├── redis.js
│   └── ...
│
├── package.json                  # Node.js dependencies and scripts.
├── server.js                     # Main server entry point.
├── worker.js                     # Background task worker.
├── .env                          # Environment variables file.
└── README.md                     # Project documentation.
```

---

## **Requirements**
To run this project, ensure you have the following installed:
- **Node.js** (v12.x or higher)
- **MongoDB** (database storage)
- **Redis** (caching system)

---

## **Setup**

1. **Clone the Repository**
   ```bash
   git clone https://github.com/lebogangolifant/alx-files_manager.git
   cd alx-files_manager
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Configure Environment Variables**
   - Create a `.env` file in the project root directory.
   - Define the following variables in the `.env` file:

     ```plaintext
     DB_HOST=<MongoDB connection URL>
     DB_NAME=<MongoDB database name>
     REDIS_HOST=<Redis server host>
     REDIS_PORT=<Redis server port>
     ```

   Example `.env` file:
   ```plaintext
   DB_HOST=mongodb://localhost:27017
   DB_NAME=mydatabase
   REDIS_HOST=localhost
   REDIS_PORT=6379
   ```

   **Note**: Keep the `.env` file secure and avoid committing it to version control.

---

## **Usage**

1. **Start the Server**
   ```bash
   npm start
   ```

2. **Access API Endpoints**  
   Use tools like **Postman** or **cURL** to interact with the API.

---

## **Endpoints**

The application provides the following API endpoints:

### **User Management**
- **`POST /users`**: Register a new user and send a welcome email.
- **`GET /connect`**: Authenticate a user and obtain a token.
- **`GET /disconnect`**: Log out a user and invalidate their token.
- **`GET /users/me`**: Retrieve the details of the currently logged-in user.

### **File Management**
- **`POST /files`**: Upload a new file.
- **`GET /files/:id`**: Get details of a specific file.
- **`GET /files`**: Retrieve a paginated list of all files.
- **`PUT /files/:id/publish`**: Publish a file.
- **`PUT /files/:id/unpublish`**: Unpublish a file.
- **`GET /files/:id/data`**: Retrieve the content of a file.
- **`GET /files/:id/data?size={size}`**: Retrieve resized content of an image file.

---

## **Testing**

To run tests for the application:

1. Install testing dependencies:
   ```bash
   npm install --save-dev jest
   ```

2. Execute tests:
   ```bash
   npm test
   ```

---

## **Notes**
- Ensure both MongoDB and Redis servers are running locally or accessible remotely.
- For background tasks (e.g., thumbnail generation), the **worker.js** script must be running alongside the server.
