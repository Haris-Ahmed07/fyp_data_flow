---

# **Sensor Data Management System**

A complete solution for managing and displaying sensor data, consisting of:

1. An **Express.js-based REST API** for storing and retrieving sensor data.
2. A **Python-based command-line application** to interact with the API, allowing users to add and view data in a visually appealing format.

---

## **Features**

### **Backend (API)**
- **Add Sensor Data**: Save sensor data (user ID, heart rate, accelerometer values, and timestamp) to a MongoDB Atlas database.
- **Retrieve Sensor Data**: Fetch all stored sensor data through an API endpoint.
- **Default Timestamps**: Automatically generate a timestamp for each record if not provided.

### **Frontend (Python Client)**
- **Add Sensor Data**: Input user ID, heart rate, and accelerometer values to send data to the API for storage.
- **Display Sensor Data**: Fetch and display all stored sensor data in a table format using the `rich` library.
- **Interactive Menu**: A user-friendly interface to interact with the system.

---

## **Table of Contents**
- [Features](#features)
- [Installation](#installation)
- [Backend Setup (API)](#backend-setup-api)
- [Frontend Setup (Python Client)](#frontend-setup-python-client)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Technologies Used](#technologies-used)
- [Future Enhancements](#future-enhancements)
- [License](#license)

---

## **Installation**

### **Prerequisites**
1. **Node.js**: Download and install from [Node.js official website](https://nodejs.org/).
2. **Python**: Download and install from [Python official website](https://www.python.org/).
3. **MongoDB Atlas**: Set up a free MongoDB Atlas cluster:
   - Create a cluster.
   - Whitelist your IP.
   - Obtain the connection string.

---

## **Backend Setup (API)**

1. Clone the repository:
   ```bash
   git clone https://github.com/Haris-Ahmed07/fyp_data_flow.git
   cd fyp_data_flow/express_api
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up your environment variables:
   - Create a `.env` file in the `express_api` directory and configure it as follows:
     ```plaintext
     PORT=5000
     MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/<database>?retryWrites=true&w=majority
     ```
     - Replace `<username>`, `<password>`, and `<database>` with your MongoDB Atlas credentials.

4. Start the server:
   ```bash
   node server.js
   ```

5. Test the API using Postman or `cURL`:
   - **Add Sensor Data**:
     ```bash
     curl -X POST http://localhost:5000/api/data \
     -H "Content-Type: application/json" \
     -d '{
         "user_id": "12345",
         "heart_rate": 72,
         "accelerometer": { "x": 10, "y": 15, "z": 20 }
     }'
     ```
   - **Retrieve All Sensor Data**:
     ```bash
     curl -X GET http://localhost:5000/api/data
     ```

---

## **Frontend Setup (Python Client)**

1. Navigate to the Python client folder:
   ```bash
   cd ../fyp_data_flow/ai_model
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate      # On macOS/Linux
   venv\Scripts\activate         # On Windows
   ```

3. Install the required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the Python application:
   ```bash
   python main.py
   ```

---

## **Usage**

### **Backend (API)**
- Once the server is running, the API will be accessible at `http://localhost:5000/api`.
- Endpoints:
  - **POST /api/data**: Add new sensor data.
  - **GET /api/data**: Retrieve all stored sensor data.

### **Frontend (Python Client)**
- Use the interactive menu:
  - Press `1` to add new sensor data.
  - Press `2` to fetch and display all stored sensor data.
  - Press `3` to exit the application.

---

## **File Structure**

```
project/
├── express_api/                 # Backend (Express API)
│   ├── models/
│   │   └── SensorData.js        # MongoDB schema for sensor data
│   ├── routes/
│   │   └── sensorRoutes.js      # API routes for adding and fetching data
│   ├── server.js                # Main server file
│   ├── .env                     # Environment variables
│   ├── package.json             # Node.js dependencies
│   └── README.md                # API documentation
├── fyp_data_flow/               # Frontend (Python Client)
│   ├── main.py                  # Entry point for the application
│   ├── api.py                   # Handles interactions with the REST API
│   ├── menu.py                  # Displays the interactive menu
│   ├── utils.py                 # Utility functions (e.g., timestamp generation)
│   ├── requirements.txt         # Python dependencies
│   └── README.md                # Python client documentation
```

---

## **Technologies Used**

### **Backend**
- **Node.js**: JavaScript runtime for the server.
- **Express.js**: Web framework for building the REST API.
- **MongoDB Atlas**: Cloud-hosted database for storing sensor data.
- **Mongoose**: MongoDB object modeling for Node.js.
- **dotenv**: For managing environment variables.

### **Frontend**
- **Python**: Core programming language for the application.
- **Requests**: For making HTTP requests to the API.
- **Rich**: For displaying visually appealing tables in the terminal.

---

## **Future Enhancements**
- **Backend**:
  - Add input validation using `Joi`.
  - Secure endpoints with JWT authentication.
  - Implement pagination for large datasets.
- **Frontend**:
  - Add data validation for user inputs.
  - Integrate with real-time sensor data streams.
  - Build a GUI for the application.

---

## **License**

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
