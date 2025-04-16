# SnapyChat
Areal time chat app with messaging.


# Task Manager - Full Stack Project

A professional lightweight full-stack Task Manager application that allows users to organize their work into Projects and Tasks.

## Features

- Create and manage projects with name and description
- Create tasks assigned to projects with title, status, and due date
- Mark tasks as complete
- View project statistics (task count, completion percentage)
- Dockerized application for easy deployment

## Tech Stack

### Backend
- Python 3.11
- FastAPI
- SQLAlchemy
- SQLite database

### Frontend
- React 18
- TypeScript
- Tailwind CSS
- Shadcn/UI components
- Redux Toolkit for state management

## Setup Instructions

### Prerequisites
- Node.js 16+ and npm/yarn
- Python 3.8+
- Docker and Docker Compose (optional, for containerized setup)

### Option 1: Local Development Setup

#### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd task-manager/backend
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   ```

3. Activate the virtual environment:
   - Windows: `venv\Scripts\activate`
   - macOS/Linux: `source venv/bin/activate`

4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

5. Start the backend server:
   ```bash
   uvicorn app.main:app --reload
   ```

   The backend will be available at http://localhost:8000

6. API Documentation:
   - Swagger UI: http://localhost:8000/docs
   - ReDoc: http://localhost:8000/redoc

#### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd task-manager/frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn install
   ```

3. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

   The frontend will be available at http://localhost:5173

### Option 2: Docker Setup

1. Make sure Docker and Docker Compose are installed on your system

2. From the project root directory, build and start the containers:
   ```bash
   docker-compose up --build
   ```

3. Access the application:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs

## Database Setup

The SQLite database will be automatically created when you first run the backend. To interact with it:

1. Install the SQLite extension for VS Code
2. Right-click on the `task_manager.db` file and select "Open Database"
3. Use the SQLITE EXPLORER in VS Code to view and query tables

## Project Structure

```
task-manager/
├── backend/
│   ├── app/
│   │   ├── models.py        # SQLAlchemy models
│   │   ├── database.py      # Database connection setup
│   │   ├── main.py          # FastAPI application
│   │   └── routers/         # API route handlers
│   │       ├── projects.py
│   │       └── tasks.py
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── components/      # React components
│   │   ├── features/        # Redux features
│   │   │   ├── projects/
│   │   │   └── tasks/
│   │   ├── store/           # Redux store setup
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── Dockerfile
│   └── package.json
└── docker-compose.yml
```

## Notes & Design Decisions

### Architecture Decisions

1. **SQLite Database**: 
   - Used SQLite for simplicity in development and demonstration
   - For production, consider PostgreSQL or MySQL for better scalability and concurrent access

2. **FastAPI Backend**:
   - FastAPI provides automatic API documentation
   - Async support for better performance under load
   - Easy validation with Pydantic models

3. **Redux Toolkit**:
   - Centralized state management for better organization
   - Simplified async operations with createAsyncThunk
   - Easy tracking of loading states and errors

4. **ShadCN/UI Components**:
   - Accessible components built on Radix UI primitives
   - Consistent styling with Tailwind CSS
   - Customizable while maintaining a professional appearance

### Challenges & Solutions

1. **State Management**:
   - Challenge: Keeping project stats in sync when tasks are updated
   - Solution: Used Redux actions to update both tasks and project statistics

2. **Form Validation**:
   - Challenge: Ensuring data quality
   - Solution: Implemented both frontend and backend validation

3. **Optimistic Updates**:
   - Challenge: Providing a responsive UI experience
   - Solution: Immediately updating UI state before waiting for API response

### Future Improvements

1. **Authentication & User Management**:
   - Add user accounts with JWT authentication
   - Project sharing and collaboration features

2. **Advanced Task Features**:
   - Task priorities
   - Task dependencies
   - Recurring tasks

3. **Data Persistence & Scaling**:
   - Migrate to PostgreSQL for better concurrent access
   - Add caching layer for frequently accessed data

4. **UI Enhancements**:
   - Drag-and-drop task reordering
   - Advanced filtering and searching
   - Calendar view for due dates

## License

MIT
