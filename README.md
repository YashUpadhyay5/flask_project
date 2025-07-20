# flask_project
# Flask Content Management System (CMS)

A simple Content Management System (CMS) built with Flask. Provides RESTful APIs for managing articles with JWT authentication.

## Docker Commands

bash
# Start the application
docker-compose up --build

# Run in background
docker-compose up -d --build

# Stop the application
docker-compose down

# View logs
docker-compose logs -f


The app will be available at [http://localhost:5000](http://localhost:5000)

## API Testing with Postman

### Setup
1. Open Postman
2. Set base URL: http://localhost:5000
3. Create environment variable: auth_token (will be set after login)

### Endpoints

#### 1. Register User
- *Method*: POST
- *URL*: http://localhost:5000/register
- *Headers*: Content-Type: application/json
- *Body*:
json
{
  "username": "testuser"
}


#### 2. Login User
- *Method*: POST
- *URL*: http://localhost:5000/login
- *Headers*: Content-Type: application/json
- *Body*:
json
{
  "username": "testuser"
}

- *Note*: Copy the token from response and set it as auth_token variable

#### 3. Create Article
- *Method*: POST
- *URL*: http://localhost:5000/articles
- *Headers*: 
  - Content-Type: application/json
  - Authorization: Bearer {{auth_token}}
- *Body*:
json
{
  "title": "My Article",
  "content": "Article content here"
}


#### 4. Create Articles Batch
- *Method*: POST
- *URL*: http://localhost:5000/articles/batch
- *Headers*: 
  - Content-Type: application/json
  - Authorization: Bearer {{auth_token}}
- *Body*:
json
[
  {
    "title": "Article 1",
    "content": "Content 1"
  },
  {
    "title": "Article 2", 
    "content": "Content 2"
  }
]


#### 5. Get All Articles
- *Method*: GET
- *URL*: http://localhost:5000/articles?page=1&limit=10
- *Headers*: Authorization: Bearer {{auth_token}}

#### 6. Get Article by ID
- *Method*: GET
- *URL*: http://localhost:5000/articles/1
- *Headers*: Authorization: Bearer {{auth_token}}

#### 7. Update Article
- *Method*: PUT
- *URL*: http://localhost:5000/articles/1
- *Headers*: 
  - Content-Type: application/json
  - Authorization: Bearer {{auth_token}}
- *Body*:
json
{
  "title": "Updated Title",
  "content": "Updated content"
}


#### 8. Delete Article
- *Method*: DELETE
- *URL*: http://localhost:5000/articles/1
- *Headers*: Authorization: Bearer {{auth_token}}

#### 9. Get Recently Viewed
- *Method*: GET
- *URL*: http://localhost:5000/recently_viewed
- *Headers*: Authorization: Bearer {{auth_token}}

## Testing Flow
1. Register a user
2. Login to get token
3. Create articles
4. List/view articles
5. Update articles
6. Delete articles
