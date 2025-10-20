# projektPINGUIN

A Flask-based task management API demonstrating a three-layer architecture with SQLAlchemy and PostgreSQL.

## Requirements

- Python 3.11+
- PostgreSQL database

## Installation

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Configuration

Create a `.env` file (already provided) with the database connection string:

```
DATABASE_URL=postgresql://user:password@localhost:5432/todo_db
```

Update the credentials to match your local PostgreSQL setup.

## Database Setup

Ensure the target database exists:

```bash
createdb todo_db
```

## Running the Application

Export the Flask application entry point and start the development server:

```bash
export FLASK_APP=app.main:app
flask run
```

The API will be available at `http://127.0.0.1:5000/`.

## API Endpoints

- `POST /tasks/` – create a new task
- `GET /tasks/` – retrieve all tasks
- `GET /tasks/<id>` – retrieve a task by ID
- `PUT /tasks/<id>` – update a task
- `DELETE /tasks/<id>` – remove a task

All responses are returned as JSON and include appropriate error handling for missing resources and invalid input.

## Creating Users

Use the Flask shell to create users required for task ownership:

```bash
flask shell
>>> from app.models import db
>>> from app.models.user import User
>>> db.session.add(User(username="demo", role="admin"))
>>> db.session.commit()
```
