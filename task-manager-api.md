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

GET /tasks
Host: api.taskmanager.com
X-API-KEY: your_api_key

## Endpoints

### 1. Get All Tasks
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

**Example Request (Filter by priority and sort by due date in descending order):**
```http
GET /tasks?priority=high&sort_by=due_date&order=desc
Host: api.taskmanager.com
X-API-KEY: your_api_key

###Example Response
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

