# Notes App API

**Live Deployment:** [https://search-assignment.onrender.com/](https://search-assignment.onrender.com/)  
**API Documentation:** [https://documenter.getpostman.com/view/50840953/2sBXwpMqhM](https://documenter.getpostman.com/view/50840953/2sBXwpMqhM)

## Description
A RESTful API built with Node.js, Express, and MongoDB for managing notes. This project implements comprehensive CRUD operations along with advanced querying capabilities, including case-insensitive search, filtering, sorting, and pagination. It features a master query endpoint designed to handle multiple query parameters simultaneously, demonstrating production-level API design.

## Problem Statement
In modern web applications, fetching data efficiently based on user criteria is crucial. Often, APIs struggle to handle complex, combined queries such as searching for a keyword while filtering by category, sorting by date, and paginating the results. Implementing these separately can lead to redundant endpoints and inefficient database queries.

## Solution
This project provides a robust backend solution with a unified querying mechanism. By utilizing MongoDB's aggregation and query operators (like `$regex`), the API exposes a master endpoint that dynamically constructs database queries based on the provided parameters. This ensures high performance, maintainability, and scalability for any front-end client consuming the API.

## Features
- **CRUD Operations:** Create (Single/Bulk), Read, Update (PUT/PATCH), and Delete (Single/Bulk) notes.
- **Search Capabilities:** Case-insensitive search on `title`, `content`, or both using MongoDB `$regex`.
- **Advanced Filtering & Sorting:** Filter notes by `category` or `isPinned` status, and sort them by fields like `createdAt` or `title` in ascending or descending order.
- **Pagination:** Limit and paginate results to ensure fast load times and efficient data transfer.
- **Master Query Endpoint:** A single unified endpoint supporting search, filter, sort, and pagination simultaneously.
- **Modular Architecture:** Clean separation of concerns using controllers, models, routes, and configuration files.

## Tech Stack
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB & Mongoose
- **Environment Management:** dotenv
- **Development Tool:** nodemon
- **Deployment:** Render

## Folder Structure
```text
.
├── .env.example
├── package.json
├── README.md
└── src/
    ├── app.js                 # Express app setup and middleware configuration
    ├── index.js               # Entry point and server initialization
    ├── config/
    │   └── db.js              # MongoDB connection setup
    ├── controllers/
    │   └── note.controller.js # Request handling and business logic
    ├── models/
    │   └── note.model.js      # Mongoose schema and model definition
    └── routes/
        └── note.routes.js     # API route definitions
```

## API Endpoints

### CRUD Operations
| Method   | Endpoint           | Description              |
|----------|--------------------|--------------------------|
| `POST`   | `/api/notes`       | Create a single note     |
| `POST`   | `/api/notes/bulk`  | Create multiple notes    |
| `GET`    | `/api/notes`       | Get all notes            |
| `GET`    | `/api/notes/:id`   | Get note by ID           |
| `PUT`    | `/api/notes/:id`   | Full replace of a note   |
| `PATCH`  | `/api/notes/:id`   | Partial update of a note |
| `DELETE` | `/api/notes/:id`   | Delete a single note     |
| `DELETE` | `/api/notes/bulk`  | Delete multiple notes    |

### Search Endpoints
| Method   | Endpoint                     | Description                           |
|----------|------------------------------|---------------------------------------|
| `GET`    | `/api/notes/search`          | Search notes by title                 |
| `GET`    | `/api/notes/search/content`  | Search notes by content               |
| `GET`    | `/api/notes/search/all`      | Search notes by title AND content     |

### Combined Query Endpoints
| Method   | Endpoint                             | Description                                      |
|----------|--------------------------------------|--------------------------------------------------|
| `GET`    | `/api/notes/filter-sort`             | Query params (category/isPinned) + Sorting       |
| `GET`    | `/api/notes/filter-paginate`         | Query params + Pagination                        |
| `GET`    | `/api/notes/sort-paginate`           | Sorting + Pagination                             |
| `GET`    | `/api/notes/search-filter`           | Search + Query params                            |
| `GET`    | `/api/notes/search-sort-paginate`    | Search + Sort + Paginate                         |
| `GET`    | `/api/notes/filter-sort-paginate`    | Filter + Sort + Paginate                         |
| `GET`    | `/api/notes/query`                   | **Master Endpoint:** Search, Filter, Sort, Limit |

## Local Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/daksh006v/search-assignment.git
   cd search-assignment
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**
   Create a `.env` file in the root directory based on `.env.example` and add your MongoDB URI:
   ```env
   PORT=3000
   MONGO_URI=your_mongodb_connection_string
   ```

4. **Start the server**
   - For development (with nodemon):
     ```bash
     npm run dev
     ```
   - For production:
     ```bash
     npm start
     ```
