# Notes App API (Search, Filter, Sort, Paginate)

This is a RESTful API built with Node.js, Express, and MongoDB. It implements comprehensive CRUD operations along with advanced querying capabilities, including MongoDB `$regex` search, filtering, sorting, and pagination. 

This project was built from scratch to demonstrate production-level API design and query combinations.

## 🚀 Live URL
**Deployed Backend:** [https://search-assignment.onrender.com/](https://search-assignment.onrender.com/)

## 🛠️ Tech Stack
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB & Mongoose
- **Deployment:** Render

## 📋 Features
1. **CRUD Operations:** Create (Single/Bulk), Read, Update (PUT/PATCH), Delete (Single/Bulk).
2. **Search Capabilities:** Case-insensitive `$regex` search on `title`, `content`, or both.
3. **Advanced Queries:** Combinations of Filter + Sort, Filter + Paginate, Sort + Paginate, and Search + Filter.
4. **Master Query Endpoint:** A single unified endpoint supporting search, filter, sort, and pagination simultaneously.

## 🚏 API Endpoints

### CRUD Operations
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/notes` | Create a single note |
| `POST` | `/api/notes/bulk` | Create multiple notes |
| `GET` | `/api/notes` | Get all notes |
| `GET` | `/api/notes/:id` | Get note by ID |
| `PUT` | `/api/notes/:id` | Full replace of a note |
| `PATCH` | `/api/notes/:id` | Partial update of a note |
| `DELETE` | `/api/notes/:id` | Delete a single note |
| `DELETE` | `/api/notes/bulk` | Delete multiple notes |

### Search Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/notes/search` | Search notes by title |
| `GET` | `/api/notes/search/content`| Search notes by content |
| `GET` | `/api/notes/search/all` | Search notes by title AND content |

### Combined Query Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/notes/filter-sort` | Query params (category/isPinned) + Sorting |
| `GET` | `/api/notes/filter-paginate` | Query params + Pagination |
| `GET` | `/api/notes/sort-paginate` | Sorting + Pagination |
| `GET` | `/api/notes/search-filter` | Search + Query params |
| `GET` | `/api/notes/search-sort-paginate`| Search + Sort + Paginate |
| `GET` | `/api/notes/filter-sort-paginate`| Filter + Sort + Paginate |
| `GET` | `/api/notes/query` | **Master Endpoint:** Search + Filter + Sort + Paginate |

## 💻 Local Setup
1. Clone the repository
2. Install dependencies: `npm install`
3. Create a `.env` file based on `.env.example` and add your `MONGO_URI`
4. Start the development server: `npm run dev`
