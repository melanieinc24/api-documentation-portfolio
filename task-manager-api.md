# Task Manager API

## Overview
The **Task Manager API** allows users to create, retrieve, update, and delete tasks. This API is designed for developers who need task management functionality in their applications.

- **Base URL:** `https://api.taskmanager.com/v1`
- **Authentication:** API Key required in the request headers.

---

## Authentication
To authenticate, include your API key in the request header as shown below:

```http
X-API-KEY: your_api_key
```

**Example Request:**
```http
GET /tasks
Host: api.taskmanager.com
X-API-KEY: your_api_key
```

---

## Endpoints

### **1. Get All Tasks**
Retrieve a list of tasks.

- **URL:** `GET /tasks`
- **Authentication Required:** ✅ Yes  
- **Query Parameters:**
  | Parameter   | Type    | Required? | Description |
  |------------|--------|------------|-------------|
  | `status`   | `string` | No | Filter by task status (`pending`, `completed`). |
  | `due_date` | `date` | No | Filter by due date (format: `YYYY-MM-DD`). |
  | `priority` | `string` | No | Filter by priority (`high`, `medium`, `low`). |
  | `limit`    | `integer` | No | Number of tasks per page (default: 10). |
  | `offset`   | `integer` | No | Start index for pagination (default: 0). |
  | `sort_by`  | `string` | No | Sort by `due_date` or `priority`. |
  | `order`    | `string` | No | Sorting order: `asc` (ascending) or `desc` (descending). |

---

### **Example Request (Filter by priority and sort by due date in descending order)**
```http
GET /tasks?priority=high&sort_by=due_date&order=desc
Host: api.taskmanager.com
X-API-KEY: your_api_key
```

### **Example Response**
```json
[
  {
    "id": 1,
    "title": "Complete API documentation",
    "description": "Expand Task Manager API documentation.",
    "status": "pending",
    "priority": "high",
    "due_date": "2025-03-15"
  }
]
```

---

### **2. Get a Single Task**
Retrieve a specific task by ID.

- **URL:** `GET /tasks/{id}`
- **Authentication Required:** ✅ Yes  
- **Path Parameters:**
  | Parameter | Type    | Required? | Description |
  |----------|--------|------------|-------------|
  | `id`     | `integer` | ✅ Yes | Task ID to retrieve. |

**Example Request:**
```http
GET /tasks/1
Host: api.taskmanager.com
X-API-KEY: your_api_key
```

**Example Response:**
```json
{
  "id": 1,
  "title": "Complete API documentation",
  "description": "Expand Task Manager API documentation.",
  "status": "pending",
  "priority": "high",
  "due_date": "2025-03-15"
}
```

---

### **3. Create a Task**
Add a new task.

- **URL:** `POST /tasks`
- **Authentication Required:** ✅ Yes  
- **Request Body (JSON Format):**
```json
{
  "title": "Write API documentation",
  "description": "Expand Task Manager API documentation.",
  "status": "pending",
  "priority": "high",
  "due_date": "2025-03-20"
}
```

**Example Request:**
```http
POST /tasks
Host: api.taskmanager.com
X-API-KEY: your_api_key
Content-Type: application/json
```

**Example Response:**
```json
{
  "message": "Task created successfully",
  "task": {
    "id": 2,
    "title": "Write API documentation",
    "description": "Expand Task Manager API documentation.",
    "status": "pending",
    "priority": "high",
    "due_date": "2025-03-20"
  }
}
```

---

### **4. Update a Task**
Modify an existing task.

- **URL:** `PUT /tasks/{id}`
- **Authentication Required:** ✅ Yes  
- **Path Parameter:** `id` (integer) – The ID of the task to update.
- **Request Body:**
```json
{
  "status": "completed"
}
```

**Example Request:**
```http
PUT /tasks/2
Host: api.taskmanager.com
X-API-KEY: your_api_key
Content-Type: application/json
```

**Example Response:**
```json
{
  "message": "Task updated successfully",
  "task": {
    "id": 2,
    "title": "Write API documentation",
    "status": "completed"
  }
}
```

---

### **5. Delete a Task**
Remove a task from the system.

- **URL:** `DELETE /tasks/{id}`
- **Authentication Required:** ✅ Yes  

**Example Request:**
```http
DELETE /tasks/2
Host: api.taskmanager.com
X-API-KEY: your_api_key
```

**Example Response:**
```json
{
  "message": "Task deleted successfully"
}
```

---

## **Error Handling**
| Status Code | Meaning | Example Response |
|-------------|------------|----------------|
| `400` | Bad Request | `{ "error": "Invalid input" }` |
| `401` | Unauthorized | `{ "error": "Invalid API Key" }` |
| `403` | Forbidden | `{ "error": "You don’t have permission to access this resource." }` |
| `404` | Not Found | `{ "error": "Task not found" }` |
| `500` | Internal Server Error | `{ "error": "Something went wrong." }` |

---


