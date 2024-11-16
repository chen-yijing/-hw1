# Internet Project 1 - Basic HTTP Server Project

This project implements a basic HTTP server in **C**, designed to practice network programming. The server listens on **port 8002** and handles HTTP `GET` and `POST` requests. It serves a simple HTML webpage with a file upload form and supports static file retrieval.

---

## 🔧 Features
- **Basic HTTP Server**:
  - Handles HTTP `GET` and `POST` requests.
  - Serves static files like HTML pages and images.

- **Static File Serving**:
  - Responds to requests for an HTML page and a static image (`images.jpeg`).
  - Uses `sendfile()` to serve files efficiently.

- **File Upload Simulation**:
  - Processes `POST` requests to extract the file name from the upload form.

- **Process Management**:
  - Uses `fork()` to handle multiple clients simultaneously.
  - Prevents zombie processes with signal handling (`SIGCHLD`).

---

## 📂 Project Structure
- **`server.c`**: Main C program file implementing the server.
- **`images.jpeg`**: Image file served by the server and displayed on the webpage.

---

## 🚀 How to Run the Server
Follow these steps to compile and run the server:

### Step 1: Compile the Program
Use the following command to compile the server program:  
`gcc -o server server.c`

### Step 2: Start the Server
Run the compiled server program:  
`./server`

### Step 3: Access the Server
Open a web browser and navigate to:  
`http://<server-ip>:8002`  
Replace `<server-ip>` with the actual IP address of the server machine.

### Step 4: Test the Features
- **View the HTML Page**:  
  The server responds with a simple HTML page containing a title, an image, and a file upload form.
- **Upload a File**:  
  Use the upload form on the webpage to send a file. The server extracts the file name and prints it in the terminal:  
  `receive filename: <uploaded-file-name>`
- **Access the Image**:  
  The image (`images.jpeg`) can be accessed directly by visiting:  
  `http://<server-ip>:8002/images.jpeg`

---

## 💻 How It Works

### Server Initialization
1. Creates a socket and binds it to port **8002**.
2. Configures the server to listen for incoming connections.
3. Uses `fork()` to spawn child processes for handling individual client connections.
4. Manages signals (`SIGCHLD`) to prevent zombie processes.

### Request Handling
- **`GET /`**:  
  Responds with a pre-defined HTML webpage.
- **`GET /images.jpeg`**:  
  Serves the image file using `sendfile()`.
- **`POST /`**:  
  Parses the HTTP request body to extract the file name of the uploaded file.

### HTML Page
The HTML page served by the server includes:
- A title: "Network Programming Homework 1".
- An image: `images.jpeg`.
- A file upload form that supports `POST` requests.

### Process Management
- Each client connection is handled in a separate process created using `fork()`.
- Signals are used to clean up zombie processes (`SIGCHLD`).

---

## 📋 Example Outputs

### Server Startup
When the server starts, it prints:  
`Server listen address: 0.0.0.0:8002`

### File Upload
When a file is uploaded using the form, the server prints:  
`receive filename: example.txt`

---

## ⚠️ Limitations
- The `POST` request processing only extracts the file name and does not store the uploaded file.
- Minimal error handling for malformed HTTP requests.
- Not optimized for high-concurrency environments or large-scale applications.

---

## 📈 Future Improvements
- Implement functionality to save uploaded files.
- Enhance request parsing and error handling.
- Support additional HTTP methods and headers.
- Optimize performance for better handling of concurrent client connections.

---

## 📝 Notes
This project is intended for learning purposes, focusing on:
- **Socket programming** in C.
- **HTTP protocol basics**.
- **Client-server communication**.
