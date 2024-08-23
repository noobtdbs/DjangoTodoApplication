# Django To-Do List Application

## Introduction

Welcome to the Django To-Do List Application! This project is a simple web-based application that allows users to manage their daily tasks. It includes features like user authentication, task creation, task updates, task deletion, and viewing tasks. The backend is powered by Django, while the API endpoints are built using Django Rest Framework.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation and Setup](#installation-and-setup)
  - [Clone the Repository](#clone-the-repository)
  - [Set Up a Virtual Environment](#set-up-a-virtual-environment)
  - [Install Dependencies](#install-dependencies)
  - [Apply Migrations](#apply-migrations)
  - [Create a Superuser](#create-a-superuser)
  - [Run the Development Server](#run-the-development-server)
- [API Endpoints](#api-endpoints)
  - [Authentication](#authentication)
  - [Task Management](#task-management)
- [Using the API](#using-the-api)
- [Accessing the Admin Panel](#accessing-the-admin-panel)
- [Testing the API with Postman](#testing-the-api-with-postman)
- [Generating `requirements.txt`](#generating-requirementstxt)
- [Conclusion](#conclusion)

## Project Overview

The Django To-Do List Application is designed to help users manage their tasks effectively. Users can register, log in, and then start creating, viewing, updating, and deleting tasks. Each task has a title, description, and a completion status. The application also includes an admin panel for managing users and tasks.

## Features

- **User Authentication**: 
  - Users can sign up, log in, and log out.
  - Authentication is token-based, ensuring secure access to API endpoints.
- **Task Management**:
  - **Create Task**: Users can add new tasks with a title and description.
  - **List Tasks**: Users can view all their tasks.
  - **Update Task**: Users can modify the title, description, and completion status of tasks.
  - **Delete Task**: Users can remove tasks from their list.
- **Admin Panel**: 
  - Superusers can manage all users and tasks via the Django admin interface.

## Technologies Used

- **Django**: The web framework used for building the backend.
- **Django Rest Framework**: For building RESTful API endpoints.
- **Django Allauth**: For handling user authentication, registration, and account management.
- **dj-rest-auth**: For providing RESTful endpoints for user authentication and registration.
- **SQLite**: The default database used for development.

## Installation and Setup

### Clone the Repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/DjangoTodoApplication.git
cd DjangoTodoApplication

```

### Set Up a Virtual Environment

It is recommended to use a virtual environment to manage dependencies. Here’s how you can create and activate one:

```bash

python -m venv venv

source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

### Install Dependencies

Once the virtual environment is activated, install the required dependencies:

```bash

pip install -r requirements.txt

```

### Apply Migrations

Django uses migrations to apply changes to the database schema. Run the following commands to create the necessary database tables:

```bash
python manage.py makemigrations
python manage.py migrate
```
### Create a Superuser
A superuser account is required to access the Django admin panel. Create one by running:

```bash

python manage.py createsuperuser
```
Follow the prompts to enter a username, email, and password.

Run the Development Server
Start the Django development server to test the application locally:

```bash
python manage.py runserver
```
The application will be accessible at http://127.0.0.1:8000/.

API Endpoints
Authentication

### Register:

URL: POST /api/auth/registration/

Body: json
```
{
    "email": "youremail@example.com",
    "password1": "yourpassword",
    "password2": "yourpassword"
}
```
### Login:

URL: POST /api/auth/login/

Body: json
```
{
    "email": "youremail@example.com",
    "password": "yourpassword"
}
```
### Logout:

URL: POST /api/auth/logout/

Body: Empty {}

Task Management
List Tasks:

URL: GET /api/tasks/

Description: Returns a list of all tasks for the authenticated user.

### Create Task:

URL: POST /api/tasks/

Body: json

```
{
    "title": "Task Title",
    "description": "Task Description"
}
```
Description: Creates a new task for the authenticated user.

### Update Task:

URL: PUT /api/tasks/<id>/

Body: json

```
{
    "title": "Updated Title",
    "description": "Updated Description",
    "completed": true
}
```
Description: Updates the specified task.

### Delete Task:

URL: DELETE /api/tasks/<id>/

Description: Deletes the specified task.

### Using the API

To interact with the API, you need to include an authentication token in the request headers. The token is obtained after logging in.

### Example Authorization Header:

Authorization: Token yourauthtoken

Replace yourauthtoken with the actual token received upon login.

### Accessing the Admin Panel

The Django admin panel allows superusers to manage the application’s data.

URL: http://127.0.0.1:8000/admin/

### Login:
Use the superuser credentials created earlier.


### Generating requirements.txt

To keep track of all the dependencies required for the project, generate a requirements.txt file by running:

```bash

pip freeze > requirements.txt

```
This command will create a requirements.txt file with all installed packages listed.

### Conclusion
This Django To-Do List application provides a simple yet powerful interface for managing tasks. It covers the essential features needed in a to-do list while also incorporating secure user authentication. The project serves as a great starting point for learning Django and building RESTful APIs.