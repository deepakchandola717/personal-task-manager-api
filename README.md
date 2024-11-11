### Project: Personal Task Manager API

#### Objective:
Build a **Personal Task Manager API** that allows users to manage their daily tasks with basic features like task creation, updates, deletion, and filtering based on priority, due dates, or completion status. The API will use **MySQL** or **PostgreSQL** as the database and should be secure, modular, and production-ready.

#### Requirements:

1. **Project Setup**
   - Initialise a new Node.js project with Express.
   - Use **MySQL** or **PostgreSQL** as the database.
   - Use an **ORM** like **Sequelize** to handle database interactions (e.g., migrations, querying).
   - Create a `.env` file to manage your environment variables (e.g., `DB_URI` for database connection URI, `DB_USER`, `DB_PASSWORD`).

2. **Project Structure**:
   - Use a modular structure:
     ```
     ├── config/
     ├── controllers/
     ├── models/
     ├── migrations/
     ├── routes/
     ├── middleware/
     ├── services/
     └── app.js
     ```

3. **Database Design**:
   - Create a **User** table with fields:
     - **id**: Primary key, auto-increment
     - **username**: Unique, required
     - **email**: Unique, required
     - **password**: Required, hashed
     - **createdAt**: Timestamp
     - **updatedAt**: Timestamp

   - Create a **Task** table with fields:
     - **id**: Primary key, auto-increment
     - **title**: (String, required)
     - **description**: (Text, optional)
     - **priority**: (String, required, values: "low", "medium", "high")
     - **dueDate**: (Date, required)
     - **status**: (String, required, values: "pending", "completed")
     - **userId**: Foreign key referencing the User table
     - **createdAt**: Timestamp
     - **updatedAt**: Timestamp

   - Set up database migrations (Sequelize) to create and manage these tables.

4. **Functionalities**:

   **a. User Authentication**:
   - Users should be able to **register** and **login** using JWT-based authentication.
   - Use bcrypt to **hash passwords**.
   - Create middleware to **protect routes** that require a logged-in user.

   **b. Task Management**:
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

5. **Routes**:
   - `/auth/register`: Register a new user.
   - `/auth/login`: Log in and receive a JWT token.
   - `/tasks`: Get all tasks for the logged-in user. Accepts optional query parameters for filtering and sorting.
   - `/tasks/:id`: Get details for a specific task (only accessible by its creator).
   - `/tasks/:id`: Update a task (only accessible by its creator).
   - `/tasks/:id`: Delete a task (only accessible by its creator).

6. **Middleware**:
   - **Authentication Middleware**: Verify JWT tokens on protected routes.
   - **Error Handling Middleware**: Global error handling for the API to return standardised error responses.

7. **Database Querying**:
   - Use Sequelize to define models, run queries, and perform joins where needed.
   - For filtering and sorting, use Sequelize query options to dynamically build queries based on URL parameters.

8. **Bonus Features (Optional)**:
   - **Pagination**: Add pagination to the task listing.
   - **Task Reminders**: Set up reminders for upcoming tasks using `setTimeout` for demo purposes or email notifications.
   - **API Documentation**: Document the API using Swagger or Postman.

9. **Submission**:
   - Upload your project to GitHub and share the link.
   - Provide a README file with setup instructions, API documentation, and any relevant notes.