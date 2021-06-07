The Fozzolog is a simple blogging platform. 

The API deals with the following objects which are stored in a database on
the backend:

- flogs (Blogs/sites)
- authors
- posts

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

The API 
