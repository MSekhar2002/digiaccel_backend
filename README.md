# Task Manager API - digiaccel_backend_Assessment

A RESTful API built with Express.js and MongoDB for managing tasks. This API serves as the backend for the Task Manager application, providing endpoints for task creation, retrieval, updates, deletion, and search functionality.

## 🛠️ Technology Stack

- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MongoDB** - Database
- **Mongoose** - MongoDB object modeling
- **CORS** - Cross-Origin Resource Sharing middleware

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas URI)
- npm or yarn

### Installation

1. Clone the repository
```bash
git clone https://github.com/MSekhar2002/digiaccel_backend.git
```

2. Navigate to the project directory
```bash
cd digiaccel_backend
```

3. Install dependencies
```bash
npm install
```


4. Start the server
```bash
npm start
```

## 📝 API Documentation

### Task Schema

```javascript
{
  title: String (required),
  description: String,
  date: Date (required),
  startTime: String (required),
  endTime: String (required),
  priority: String (enum: ['Low', 'Medium', 'High'], default: 'Medium'),
  completed: Boolean (default: false),
  createdAt: Date (default: Date.now)
}
```

### Endpoints

#### Get All Tasks
```http
GET /api/tasks
```
- Returns all tasks sorted by date and start time
- Response: Array of task objects

#### Create Task
```http
POST /api/tasks
```
- Request Body: Task object
- Response: Created task object

#### Update Task
```http
PUT /api/tasks/:id
```
- Request Parameters: Task ID
- Request Body: Updated task fields
- Response: Updated task object

#### Delete Task
```http
DELETE /api/tasks/:id
```
- Request Parameters: Task ID
- Response: Deletion confirmation message

#### Search Tasks
```http
GET /api/tasks/search?q=searchterm
```
- Query Parameters: q (search term)
- Searches through title and description
- Response: Array of matching task objects

## 🔍 Example API Requests

### Create a Task
```bash
curl -X POST http://localhost:5000/api/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Team Meeting",
    "description": "Weekly sync with the team",
    "date": "2024-03-20",
    "startTime": "10:00",
    "endTime": "11:00",
    "priority": "High"
  }'
```

### Update a Task
```bash
curl -X PUT http://localhost:5000/api/tasks/taskId \
  -H "Content-Type: application/json" \
  -d '{
    "completed": true
  }'
```

### Search Tasks
```bash
curl http://localhost:5000/api/tasks/search?q=meeting
```

## 🔐 Error Handling

The API implements standard HTTP status codes:
- 200: Success
- 201: Resource created
- 400: Bad request
- 500: Server error

Error responses include a message field explaining the error:
```json
{
  "message": "Error description"
}
```


## 🧪 Testing

To run tests (when implemented):
```bash
npm test
```

## 🔄 API Response Examples

### Task Object
```json
{
  "_id": "60d3b41ef682d123e4567890",
  "title": "Team Meeting",
  "description": "Weekly sync with the team",
  "date": "2024-03-20T00:00:00.000Z",
  "startTime": "10:00",
  "endTime": "11:00",
  "priority": "High",
  "completed": false,
  "createdAt": "2024-03-19T15:00:00.000Z"
}
```

## 🔒 Security Considerations

1. CORS is enabled for cross-origin requests
2. Request body parsing is limited to JSON
3. MongoDB connection uses the latest security protocols
4. Input validation is performed through Mongoose schema

## 📦 Dependencies

```json
{
  "express": "^4.17.1",
  "mongoose": "^6.0.0",
  "cors": "^2.8.5"
}
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


---

For more information or support, please open an issue in the repository.
