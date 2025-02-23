```markdown
# API References

This document provides a detailed reference for the API endpoints available on the BITS website. It covers endpoint descriptions, request and response formats, and authentication mechanisms.

## Table of Contents
- [Authentication](#authentication)
- [Endpoints](#endpoints)
  - [Posts](#posts)
  - [Pages](#pages)
  - [Comments](#comments)
  - [Users](#users)
- [Error Handling](#error-handling)
- [Examples](#examples)

## Authentication

### Overview

The API uses token-based authentication to secure endpoints that require user credentials. For protected endpoints, include your authentication token in the HTTP header.

### Mechanisms

- **Bearer Token:**
  - Include the token in the `Authorization` header:
    ```
    Authorization: Bearer <your_token>
    ```
  - Tokens are obtained through a login endpoint (for example, using JWT Authentication for WP REST API).

- **API Key (Optional):**
  - Alternatively, some endpoints may allow passing an API key as a query parameter:
    ```
    ?api_key=<your_api_key>
    ```

## Endpoints

### Posts

#### Retrieve All Posts
- **URL:** `/wp-json/wp/v2/posts`
- **Method:** GET
- **Description:** Returns a list of published posts.
- **Request Parameters:**
  - `per_page` (integer): Number of posts per page.
  - `page` (integer): Current page number.
  - `search` (string): Filter posts by a search term.
- **Response Format:**
  ```json
  [
    {
      "id": 1,
      "date": "2023-01-01T12:00:00",
      "title": {
        "rendered": "Post Title"
      },
      "content": {
        "rendered": "<p>Post content goes here.</p>"
      },
      "excerpt": {
        "rendered": "<p>Short excerpt of the post.</p>"
      },
      "link": "http://example.com/post-title"
    },
    ...
  ]
  ```

#### Retrieve Single Post
- **URL:** `/wp-json/wp/v2/posts/{id}`
- **Method:** GET
- **Description:** Retrieves a single post by its ID.
- **Path Parameters:**
  - `id` (integer): The ID of the post.
- **Response Format:**
  ```json
  {
    "id": 1,
    "date": "2023-01-01T12:00:00",
    "title": {
      "rendered": "Post Title"
    },
    "content": {
      "rendered": "<p>Post content goes here.</p>"
    },
    "excerpt": {
      "rendered": "<p>Short excerpt of the post.</p>"
    },
    "link": "http://example.com/post-title"
  }
  ```

### Pages

#### Retrieve All Pages
- **URL:** `/wp-json/wp/v2/pages`
- **Method:** GET
- **Description:** Returns a list of pages.
- **Request Parameters:** Similar to posts (`per_page`, `page`, etc.).
- **Response Format:** Structure similar to the posts endpoint.

#### Retrieve Single Page
- **URL:** `/wp-json/wp/v2/pages/{id}`
- **Method:** GET
- **Description:** Retrieves a single page by its ID.
- **Path Parameters:**
  - `id` (integer): The ID of the page.
- **Response Format:** Similar to the single post response.

### Comments

#### Retrieve Comments for a Post
- **URL:** `/wp-json/wp/v2/comments`
- **Method:** GET
- **Description:** Returns a list of comments. Use query parameters to filter by post ID.
- **Request Parameters:**
  - `post` (integer): The ID of the post.
- **Response Format:**
  ```json
  [
    {
      "id": 101,
      "post": 1,
      "author_name": "John Doe",
      "date": "2023-01-02T14:00:00",
      "content": {
        "rendered": "<p>This is a comment.</p>"
      }
    },
    ...
  ]
  ```

### Users

#### Retrieve Current User (Protected)
- **URL:** `/wp-json/wp/v2/users/me`
- **Method:** GET
- **Description:** Retrieves details of the authenticated user.
- **Headers:**
  - `Authorization: Bearer <your_token>`
- **Response Format:**
  ```json
  {
    "id": 2,
    "name": "Jane Doe",
    "url": "http://example.com",
    "description": "A brief bio",
    "link": "http://example.com/author/janedoe"
  }
  ```

#### Retrieve User by ID (Protected)
- **URL:** `/wp-json/wp/v2/users/{id}`
- **Method:** GET
- **Description:** Retrieves details for a specific user.
- **Path Parameters:**
  - `id` (integer): The ID of the user.
- **Response Format:** Similar to the current user endpoint.

## Error Handling

### Standard Error Response

When an error occurs, the API returns a structured error message. For example:

```json
{
  "code": "rest_post_invalid_id",
  "message": "Invalid post ID.",
  "data": {
    "status": 404
  }
}
```

- HTTP status codes are used to indicate error states (e.g., 404 for not found, 401 for unauthorized).

## Examples

### Fetching Posts (cURL)
```bash
curl -X GET "http://example.com/wp-json/wp/v2/posts?per_page=5&page=1" -H "Authorization: Bearer YOUR_TOKEN"
```

### Creating a New Post (cURL)
```bash
curl -X POST "http://example.com/wp-json/wp/v2/posts" \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer YOUR_TOKEN" \
     -d '{
           "title": "New Post Title",
           "content": "This is the content of the new post.",
           "status": "publish"
         }'
```

