The Fozzolog is a simple blogging platform. 

The API deals with the following objects which are stored in a database on
the backend:

- flogs (Blogs/sites)
- authors
- posts

# Object relationships

The object relationship diagram for this schema looks like this:

    +----------------+       +----------------+
    |     flog       |       |     author     |
    +----------------+------>+----------------+
    | id             |       | id             |
    | name           |       | flog_id        |
    +----------------+       | name           |
                             | username       |
                             | password       |
                             | is_admin       |
                             | is_flog_admin  |
                             +----------------+
                                      |
                                      |
                                      |
                                      V
                             +----------------+
                             |     post       |
                             +----------------+
                             | id             |
                             | author_id      |
                             | title          |
                             | body           |
                             +----------------+

# The API

This is a fairly simple API with most API operations corresponding to CRUD 
operations on the core data objects.

The exception is `/login` which handles initial validation and
authentication of a user's credentials and returns an API key that may be
used in subsequent requests for protected paths.

## Routes/paths

### `/flogs/` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| GET       | Returns a list of all flog objects        | N         |
| POST      | Creates a new flog objects                | Y         |

### `/flogs/ID` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| GET       | Returns a single flog object              | N         |
| PUT       | Updates a single flog object              | Y         |
| DELETE    | Updates a single flog object              | Y         |

### `/authors/` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| GET       | Returns a list of all author objects      | N         |
| POST      | Creates a new author object               | Y         |

### `/authors/ID` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| GET       | Returns a single author object            | N         |
| PUT       | Updates a single author object            | Y         |
| DELETE    | Updates a single author object            | Y         |

### `/flogs/ID/posts` 

| Method    | Description                                       | Protected |
| --------- | -----------                                       | --------- |
| GET       | Returns a list of all post objects for a flog     | N         |

### `/authors/ID/posts` 

| Method    | Description                                       | Protected |
| --------- | -----------                                       | --------- |
| GET       | Returns a list of all post objects for an author  | N         |

### `/posts/` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| POST      | Creates a new post object                 | Y         |

### `/posts/ID` 

| Method    | Description                               | Protected |
| --------- | -----------                               | --------- |
| GET       | Returns a single post object              | N         |
| PUT       | Updates a single post object              | Y         |
| DELETE    | Updates a single post object              | Y         |
