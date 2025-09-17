# Blog API

A robust RESTful blog API built with Node.js, Express, and TypeScript. This API provides a complete backend solution for a blogging platform, featuring JWT authentication, role-based access control, and full CRUD (Create, Read, Update, Delete) functionality for users, blog posts, comments, and likes. It also includes Cloudinary integration for seamless media uploads.

-----

## Features

  * **User Authentication:** Secure user registration and login using JSON Web Tokens (JWT).
  * **Role-Based Access Control:** Differentiated permissions for "admin" and "user" roles, ensuring that only authorized users can perform certain actions.
  * **Blog Post Management:** Full CRUD operations for blog posts, including the ability to create, read, update, and delete posts.
  * **Media Uploads:** Integrated with Cloudinary for efficient and scalable image hosting and management for blog banners.
  * **Commenting and Likes:** Allows users to engage with blog posts by adding comments and liking or unliking them.
  * **Content Sanitization:** Uses DOMPurify to sanitize user-generated content and prevent XSS (Cross-Site Scripting) attacks.
  * **Pagination:** Supports pagination for lists of blogs and users to efficiently handle large datasets.
  * **Input Validation:** Utilizes `express-validator` to validate and sanitize incoming request data, enhancing security and data integrity.
  * **Security Headers:** Employs Helmet to set various HTTP headers, protecting the application from common web vulnerabilities.
  * **Rate Limiting:** Implements rate limiting to prevent abuse and ensure the API's availability.
  * **Comprehensive Logging:** Uses Winston and Logtail for detailed logging of application events, errors, and requests, facilitating debugging and monitoring.

-----

## Technologies Used

  * **Backend:** Node.js, Express.js
  * **Language:** TypeScript
  * **Database:** MongoDB with Mongoose
  * **Authentication:** JSON Web Tokens (JWT)
  * **Media Hosting:** Cloudinary
  * **Security:** Helmet, express-rate-limit, express-validator, DOMPurify, bcrypt
  * **Logging:** Winston, Logtail
  * **Other:** Multer, cookie-parser, cors, compression, dotenv

-----

## Prerequisites

  * Node.js (v18.x or higher recommended)
  * npm (or yarn)
  * MongoDB
  * Cloudinary Account

-----

## Installation and Setup

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd blog-api
    ```

2.  **Install dependencies:**

    ```bash
    npm install
    ```

3.  **Set up environment variables:**

    Create a `.env` file in the root of the project and add the following environment variables:

    ```
    PORT=3000
    NODE_ENV=development
    MONGO_URI=<your-mongodb-connection-string>
    JWT_ACCESS_SECRET=<your-jwt-access-secret>
    JWT_REFRESH_SECRET=<your-jwt-refresh-secret>
    ACCESS_TOKEN_EXPIRY=1h
    REFRESH_TOKEN_EXPIRY=1w
    CLOUDINARY_CLOUD_NAME=<your-cloudinary-cloud-name>
    CLOUDINARY_API_KEY=<your-cloudinary-api-key>
    CLOUDINARY_API_SECRET=<your-cloudinary-api-secret>
    LOGTAIL_SOURCE_TOKEN=<your-logtail-source-token>
    LOGTAIL_INGESTING_HOST=<your-logtail-ingesting-host>
    ```

4.  **Start the development server:**

    ```bash
    npm run dev
    ```

    The API will be running at `http://localhost:3000`.

-----

## API Endpoints

All endpoints are prefixed with `/api/v1`.

### Authentication

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/auth/register` | Register a new user. |
| `POST` | `/auth/login` | Log in an existing user and receive an access token. |
| `POST` | `/auth/refresh-token` | Obtain a new access token using a refresh token. |
| `POST` | `/auth/logout` | Log out the user and invalidate the refresh token. |

### Users

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/users/current` | Get the profile of the currently authenticated user. |
| `PUT` | `/users/current` | Update the profile of the currently authenticated user. |
| `DELETE` | `/users/current` | Delete the profile of the currently authenticated user. |
| `GET` | `/users` | Get a list of all users (admin only). |
| `GET` | `/users/:userId` | Get the profile of a specific user by their ID (admin only). |
| `DELETE` | `/users/:userId` | Delete a specific user by their ID (admin only). |

### Blogs

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/blogs` | Create a new blog post (admin only). |
| `GET` | `/blogs` | Get a list of all blog posts (published posts for users, all for admins). |
| `GET` | `/blogs/user/:userId` | Get a list of all blog posts by a specific user. |
| `GET` | `/blogs/:slug` | Get a single blog post by its slug. |
| `PUT` | `/blogs/:blogId` | Update a blog post by its ID (admin only). |
| `DELETE` | `/blogs/:blogId` | Delete a blog post by its ID (admin only). |

### Likes

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/likes/blog/:blogId` | Like a blog post. |
| `DELETE` | `/likes/blog/:blogId` | Unlike a blog post. |

### Comments

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/comments/blog/:blogId` | Add a comment to a blog post. |
| `GET` | `/comments/blog/:blogId` | Get all comments for a blog post. |
| `DELETE` | `/comments/:commentId` | Delete a comment by its ID. |

Would you like me to create a Postman collection from these API endpoints to make testing them easier?
