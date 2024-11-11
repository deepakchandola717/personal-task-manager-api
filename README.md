### Project: Personal Task Manager API

#### Objective:
Build a **Personal Task Manager API** that allows users to manage their daily tasks with basic features like task creation, updates, deletion, and filtering based on priority, due dates, or completion status. The API will use **MongoDB** as the database and should be secure, modular, and production-ready.

#### Requirements:

1. **Project Setup**
   - Initialise a new Node.js project with Express.
   - Use **MongoDB** as the database. You can use **MongoDB Atlas** for cloud-based setup or run a local MongoDB instance.
   - Create a `.env` file to manage your environment variables (e.g., `DB_URI` for MongoDB URI).

2. **Project Structure**:
   - Use a modular structure:
     ```
     ├── config/
     ├── controllers/
     ├── models/
     ├── routes/
     ├── middleware/
     ├── services/
     └── app.js
     ```

3. **Functionalities**:

   **a. User Authentication**:
   - Users should be able to **register** and **login** using JWT-based authentication.
   - Use bcrypt to **hash passwords**.
   - Create middleware to **protect routes** that require a logged-in user.

   **b. Task Management**:
   - Each task should have:
     - **title**: (String, required)
     - **description**: (String, optional)
     - **priority**: (String, required, values: "low", "medium", "high")
     - **dueDate**: (Date, required)
     - **status**: (String, required, values: "pending", "completed")
     - **createdAt**: (Date, default to now)
     - **updatedAt**: (Date, auto-update when modified)
     - **userId**: Reference to the User who created the task

   - Implement CRUD operations for tasks:
     - **Create a Task**: Only authenticated users can create tasks.
     - **View Tasks**: Retrieve all tasks belonging to the authenticated user.
     - **Update a Task**: Allow updates to title, description, priority, due date, and status.
     - **Delete a Task**: Only the creator of the task can delete it.

   **c. Filtering and Sorting**:
   - Allow filtering of tasks by:
     - **priority** (low, medium, high)
     - **dueDate range**
     - **status** (pending, completed)
   - Allow sorting by:
     - **dueDate** (ascending/descending)
     - **priority**

   **d. Error Handling**:
   - Implement error handling for common scenarios (e.g., invalid data, unauthorised access, missing fields).
   - Use custom error messages to improve user feedback.

4. **Routes**:
   - `/auth/register`: Register a new user.
   - `/auth/login`: Log in and receive a JWT token.
   - `/tasks`: Get all tasks for the logged-in user. Accepts optional query parameters for filtering and sorting.
   - `/tasks/:id`: Get details for a specific task (only accessible by its creator).
   - `/tasks/:id`: Update a task (only accessible by its creator).
   - `/tasks/:id`: Delete a task (only accessible by its creator).

5. **Middleware**:
   - **Authentication Middleware**: Verify JWT tokens on protected routes.
   - **Error Handling Middleware**: Global error handling for the API to return standardised error responses.

6. **Database Schema**:
   - Define separate schemas for **User** and **Task** models.
   - Use Mongoose's built-in schema validation for data integrity.

7. **Bonus Features (Optional)**:
   - **Pagination**: Add pagination to the task listing.
   - **Task Reminders**: Send an email reminder for upcoming tasks (consider using Node's built-in `setTimeout` for demo purposes).
   - **API Documentation**: Document the API using Swagger or Postman.

8. **Submission**:
   - Upload your project to GitHub and share the link.
   - Provide a README file with setup instructions, API documentation, and any relevant notes.