
# Django REST API – Blog Post Management System

## 📌 Project Overview

This project is a RESTful API for managing blog posts, built using Python, Django, and Django REST Framework (DRF).

The API enables authenticated users to create, retrieve, update, and delete blog posts. It includes user-based permissions to ensure that users can modify only their own posts, along with filtering, searching, ordering, and pagination features.

The project uses SQLite as its database and supports Django authentication and the Django REST Framework Browsable API.

## 🎯 Project Objectives

- Build a RESTful API using Django REST Framework.
- Implement CRUD operations for blog posts.
- Authenticate users using Django and DRF authentication mechanisms.
- Restrict users to accessing and modifying their own posts.
- Filter posts by creation date.
- Search posts by title and content.
- Order posts by ID.
- Implement pagination with five posts per page.
- Return structured API responses in JSON format.

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Programming Language | Python 3 |
| Backend Framework | Django 6.0.1 |
| REST API Framework | Django REST Framework |
| Filtering | django-filter |
| Database | SQLite3 |
| Authentication | Django Session Authentication / DRF authentication |
| API Interface | DRF Browsable API |
| Data Format | JSON |

## ✨ Key Features

### 1. CRUD Operations

The API supports the following operations:

- **Create:** Add a new blog post.
- **Read:** Retrieve accessible blog posts.
- **Update:** Modify an existing blog post.
- **Delete:** Remove a blog post.

### 2. User Authentication

The API uses Django authentication to identify users and restrict protected operations to authenticated users.

Depending on the configured authentication classes, users can authenticate through session-based authentication or other supported mechanisms.

### 3. Custom Permissions

Custom permission logic ensures that authenticated users can update or delete only their own blog posts.

Post ownership is associated with the authenticated user who created the post.

### 4. Filtering

Users can filter blog posts by creation date using the configured `django-filter` functionality.

### 5. Searching

The API supports searching blog posts by:

- Title
- Content

### 6. Ordering

Blog posts can be ordered by their ID in ascending or descending order, depending on the requested ordering parameter.

### 7. Pagination

The API returns a maximum of **5 blog posts per page**, making large collections easier to browse.

### 8. JSON Responses

The API provides structured responses suitable for frontend applications, API clients, and other services.

## 📂 Project Structure

```text
DjangoRestAPI-YourName/
│
└── blog/
    ├── blog/
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── urls.py
    │   ├── wsgi.py
    │   └── asgi.py
    │
    ├── helloworld/
    │   ├── migrations/
    │   │   └── __init__.py
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py
    │   ├── views.py
    │   ├── serializers.py
    │   ├── permissions.py
    │   ├── filters.py
    │   └── tests.py
    │
    ├── manage.py
    └── db.sqlite3
```

**Important files:**

- `manage.py` – Runs Django management commands.
- `settings.py` – Contains project configuration and installed applications.
- `urls.py` – Defines project-level and application-level URL routes.
- `models.py` – Defines the blog post database model.
- `views.py` – Implements API endpoints and CRUD functionality.
- `serializers.py` – Converts model instances to and from API representations.
- `permissions.py` – Defines custom access-control rules.
- `filters.py` – Implements custom filtering logic, if required.
- `tests.py` – Contains automated tests.
- `db.sqlite3` – Stores the SQLite database and project data.

The exact folder structure may vary slightly depending on how the Django project was created.

## ⚙️ Installation and Setup

### Step 1: Install Python

Install Python from [python.org](https://www.python.org/downloads/) if it is not already installed.

Check the installation:

```bash
python --version
```

### Step 2: Navigate to the Project Folder

Open Command Prompt or the VS Code terminal and navigate to the directory containing `manage.py`.

```bash
cd path/to/DjangoRestAPI-YourName/blog
```

Replace the example path with your actual project location.

### Step 3: Create a Virtual Environment (Recommended)

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### Step 4: Install Required Packages

```bash
python -m pip install django==6.0.1 djangorestframework django-filter
```

If your project uses token authentication, install and configure DRF's token authentication as well. If it uses only session authentication, token authentication is not required.

### Step 5: Apply Database Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

If migrations already exist, apply them using `python manage.py migrate`.

### Step 6: Create a Superuser

```bash
python manage.py createsuperuser
```

Follow the prompts to create an administrator account.

### Step 7: Start the Development Server

```bash
python manage.py runserver
```

Open the application in your browser:

- **API root:** `http://127.0.0.1:8000/`
- **Django admin:** `http://127.0.0.1:8000/admin/`

The exact API endpoint URLs depend on the routes configured in your project.

## 🔗 API Functionality

The following table describes the expected endpoint patterns. Replace `/api/posts/` with the actual URL configured in your project if it differs.

| HTTP Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/posts/` | List accessible blog posts |
| POST | `/api/posts/` | Create a blog post |
| GET | `/api/posts/{id}/` | Retrieve an individual post |
| PUT | `/api/posts/{id}/` | Update an individual post |
| PATCH | `/api/posts/{id}/` | Partially update a post |
| DELETE | `/api/posts/{id}/` | Delete an individual post |

Protected endpoints require authentication according to the project's configured permissions.

## 🔍 Filtering, Searching, and Ordering

The following are illustrative query patterns, assuming these parameters are configured in the API.

### Filter by Creation Date

```text
/api/posts/?created_at=2026-10-15
```

The actual parameter names and supported date ranges depend on the implementation in `filters.py`.

### Search by Title or Content

```text
/api/posts/?search=Python
```

This searches configured searchable fields, such as title and content.

### Order by ID

```text
/api/posts/?ordering=id
```

For descending ID order:

```text
/api/posts/?ordering=-id
```

### Pagination

```text
/api/posts/?page=1
```

The response should contain up to five posts per page, together with pagination metadata when configured.

## 🧪 Testing the API

After starting the server, test the API using the DRF Browsable API, Django admin, or a tool such as Postman.

Verify the following:

1. Unauthenticated users cannot perform protected operations.
2. Authenticated users can create blog posts.
3. Users can retrieve posts permitted by the configured access rules.
4. Users cannot update or delete another user's posts.
5. Filtering by creation date returns the expected results.
6. Searching works for titles and content.
7. Ordering works in ascending and descending order.
8. Pagination returns no more than five posts per page.
9. Successful requests and errors return appropriate responses.

## 🧠 Learning Outcomes

Through this project, I practiced:

- Building REST APIs with Django REST Framework.
- Implementing CRUD operations.
- Working with Django models and serializers.
- Configuring authentication and custom permissions.
- Enforcing user-based object access.
- Implementing filtering, searching, ordering, and pagination.
- Working with SQLite databases.
- Testing API endpoints and handling HTTP requests and responses.

## 🔐 Security Considerations

- Require authentication for protected endpoints.
- Enforce object-level permissions on individual blog posts.
- Validate incoming data through serializers.
- Keep secret keys and credentials out of public repositories.
- Do not commit production database credentials or sensitive user data.
- Use appropriate production security settings before deploying the application.

## 📦 Submission Instructions

1. Create a main folder named `DjangoRestAPI-YourName`.
2. Include the complete Django project and application files.
3. Include `manage.py`, the required Python modules, migrations, and `db.sqlite3` as specified in the assignment.
4. Test the application and verify the API endpoints.
5. Compress the main folder into a ZIP file.
6. Open the ZIP file to verify that the required files are present.
7. Upload the ZIP file to the assignment submission portal.

**Note:** Keep `db.sqlite3` in the submission ZIP as required by the assignment. Do not include your virtual environment folder; the required packages can be installed separately.

## 📌 Conclusion

The Django REST API project demonstrates how to build a blog post management system with authentication, user-specific permissions
