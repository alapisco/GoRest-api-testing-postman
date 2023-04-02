# GoRest API Tests in Postman

This contains a postman collection, file `GoRest API Testing.postman_collection.json` , that performs tests on the 4 REST API resources available on https://gorest.co.in/     

- /public/v2/users
- /public/v2/posts
- /public/v2/comments
- /public/v2/todos

CRUD tests are included in the collection for all endpoints.

Main focus is put on the `/public/v2/users`.

Tests for the `users endpoint` also include
 - Additional functional tests
 - Negative tests
 - Edge tests 

## Table of Contents

1. [Running the Tests](#running-the-tests)
    -  [Postman](#postman)
    -  [Newman](#newman)
2. [The GoRest API Testing collection](#the-gorest-api-testing-collection)
    -  [Functional Testing](#functional-testing)
        - [Users CRUD](#users-crud)
        - [Posts CRUD](#posts-crud)
        - [Comments CRUD](#comments-crud)
        - [Todos CRUD](#todos-crud)
        - [Users Pagination](#users-pagination)
        - [Users Search](#users-search)
    -  [Users - Negative Testing](#users---negative-testing)    
        - [Pagination](#pagination)
        - [Search](#pagination)
        - [Create User](#pagination)

## Running the tests

### Postman

You can use the `web version` or the `Desktop application` of `Postman`

For details on how to install Postman, go to the [Official Documentation](https://learning.postman.com/docs/getting-started/installation-and-updates/)


### Importing the Postman Collection

To import the exported collection file into Postman, follow these steps:

- Open Postman.
- In the top-left corner, click the "Import" button.
- A new dialog will appear. Click "Upload Files" and select the exported collection file (it should have a .json extension) from your computer, or drag and drop the file into the dialog box.
- After the file is uploaded, Postman will display `GoRest API Testing` , under the "Collections" tab.


### Running the Tests
To run the tests in the imported Postman collection, follow these steps:

- Select a request from the collection in the left sidebar.
- Click the "Run" option in the `...` button 
- Click the `Run GoRest API Testing` button

### Newman

`Newman` is  Node JS command line applicaiton that allows running `Postman collections` from the console in headless mode.

To install Newman on your OS refer to the [Official Documentation](https://learning.postman.com/docs/collections/using-newman-cli/installing-running-newman/)

### Running the Tests

Execute the following command

```bash
newman run <path-to-postman-collection-file>
```

Example, form the project root dir:

```bash
 newman run '.\GoRest API Testing.postman_collection.json'
```

You will see the enponts being executed sequentially , along with their tests, and tests status.


The results of all tests and requests can be exported into a file. Use the JSON reporter and a file name to save the output into a file.

```bash
newman run mycollection.json --reporters cli,json --reporter-json-export outputfile.json
```


## The `GoRest API Testing` collection

Tests in the collection are divided in the following folders:

### Functional Testing

Contains CRUD tests for all endpoints

### Users CRUD

This folder contains tests with data and error validation on requests
that do the following operations

 - Creates a new user
 - Get new user details
 - Update user using PUT
 - Update user using PATCH
 - Deletes User
 - Checks deleted user 

### Posts CRUD

This folder contains tests with data and error validation on requests
that do the following operations

 - Creates a new user
 - Creates a new post assigned to that user
 - Get new post details
 - Update post using PUT
 - Update post using PATCH
 - Deletes post
 - Checks deleted post 

### Comments CRUD

This folder contains tests with data and error validation on requests
that do the following operations

 - Creates a new post assigned to the user created on Posts CRUD flow
 - Creates a new comment on that post
 - Get new comment details
 - Update comment using PUT
 - Update comment using PATCH
 - Deletes comment
 - Checks deleted comment 

### Todos CRUD

This folder contains tests with data and error validation on requests
that do the following operations

 - Creates a new todo assigned to the user created on Posts CRUD flow
 - Get new todo details
 - Update todo using PUT
 - Update todo using PATCH
 - Deletes todo
 - Checks deleted todo 

### Users Pagination

Contains pagination `header tests`, and tests for parameters
`page` and `per_page`

### Users Search

Contains tests for requests that:
- search users by name
- search user by id
- search user by email
- search users by gender
- search users by status

### Users - Negative Testing

Contains tests for invalid input or unexpected user behavior

### Pagination

- Request with page that exceeds the total pages available
- Request with page 0
- Request with negative page
- Request with invalid page (ex page=abc)
- Request with empty page

### Search

Contains negative tests for users search by all field and also
not existing fields


### Create User

Contains negative tests for empty, invalid values, or special characters used when creating a user