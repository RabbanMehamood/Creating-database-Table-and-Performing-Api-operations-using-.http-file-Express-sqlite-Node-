# Todo Application

Given an `app.js` file and an empty database file `todoApplication.db`.

Create a table with the name `todo` with the following columns,

**Todo Table**

| Column   | Type    |
| -------- | ------- |
| id       | INTEGER |
| todo     | TEXT    |
| priority | TEXT    |
| status   | TEXT    |

and write APIs to perform operations on the table `todo`,

How to create and insert the data into the table.
You can create and insert the data into a database using the SQLite CLI.

You can write and execute SQL queries using SQLite CLI to retrieve, insert, update, or delete data in the database tables.

Insert the data in the todo table using the given data.


In the todo table for the column id, insert the integer value based on the number of todos existing in the table todo

For column todo, insert any text

The possible values of the columns priority & status are mentioned in the Note point as shown below.


Once refer to the below screenshot to understand how to create and insert the data into a database using the SQLite CLI.

 Terminal 1 X
root@6e1e2d6c2643:/home/workspace/nodejs/coding-practices/coding-practice-8a# sqlite3 todoApplication.db
SQLite version 3.16.2 2017-01-06 16:32:41
Enter ".help" for usage hints.
sqlite> CREATE TABLE todo (id INTEGER, todo TEXT, priority TEXT, status TEXT);
sqlite> INSERT INTO todo (id, todo, priority, status)
...> Values (1, "Learn HTML", "HIGH", "TO DO"),
(2, "Learn JS", "MEDIUM", "DONE"),
...> (3, "Learn CSS", "LOW", "DONE");
sqlite> SELECT from todo;
1| Learn HTML HIGH TO DO
2| Learn JS MEDIUM DONE
3| Learn CSS LOW DONE
sqlite> - did not match any documents.


<MultiLineNote>
  
  - Replace the spaces in URL with `%20`.
  - Possible values for `priority` are `HIGH`, `MEDIUM`, and `LOW`.
  - Possible values for `status` are `TO DO`, `IN PROGRESS`, and `DONE`.
</MultiLineNote>

### API 1

#### Path: `/todos/`

#### Method: `GET`

- **Scenario 1**

  - **Sample API**
    ```
    /todos/?status=TO%20DO
    ```
  - **Description**:

    Returns a list of all todos whose status is 'TO DO'

  - **Response**

    ```
    [
      {
        id: 1,
        todo: "Watch Movie",
        priority: "LOW",
        status: "TO DO"
      },
      ...
    ]
    ```

- **Scenario 2**

  - **Sample API**
    ```
    /todos/?priority=HIGH
    ```
  - **Description**:

    Returns a list of all todos whose priority is 'HIGH'

  - **Response**

    ```
    [
      {
        id: 2,
        todo: "Learn Node JS",
        priority: "HIGH",
        status: "IN PROGRESS"
      },
      ...
    ]
    ```

- **Scenario 3**

  - **Sample API**
    ```
    /todos/?priority=HIGH&status=IN%20PROGRESS
    ```
  - **Description**:

    Returns a list of all todos whose priority is 'HIGH' and status is 'IN PROGRESS'

  - **Response**

    ```
    [
      {
        id: 2,
        todo: "Learn Node JS",
        priority: "HIGH",
        status: "IN PROGRESS"
      },
      ...
    ]
    ```

- **Scenario 4**

  - **Sample API**
    ```
    /todos/?search_q=Play
    ```
  - **Description**:

    Returns a list of all todos whose todo contains 'Play' text

  - **Response**

    ```
    [
      {
        id: 4,
        todo: "Play volleyball",
        priority: "MEDIUM",
        status: "DONE"
      },
      ...
    ]
    ```

### API 2

#### Path: `/todos/:todoId/`

#### Method: `GET`

#### Description:

Returns a specific todo based on the todo ID

#### Response

```
{
  id: 2,
  todo: "Learn JavaScript",
  priority: "HIGH",
  status: "DONE"
}
```

### API 3

#### Path: `/todos/`

#### Method: `POST`

#### Description:

Create a todo in the todo table,

#### Request

```
{
  "id": 10,
  "todo": "Finalize event theme",
  "priority": "LOW",
  "status": "TO DO"
}
```

#### Response

```
Todo Successfully Added
```

### API 4

#### Path: `/todos/:todoId/`

#### Method: `PUT`

#### Description:

Updates the details of a specific todo based on the todo ID

- **Scenario 1**

  - **Request**
    ```
    {
      "status": "DONE"
    }
    ```
  - **Response**

    ```
    Status Updated
    ```

- **Scenario 2**

  - **Request**
    ```
    {
      "priority": "HIGH"
    }
    ```
  - **Response**

    ```
    Priority Updated
    ```

- **Scenario 3**

  - **Request**
    ```
    {
      "todo": "Some task"
    }
    ```
  - **Response**

    ```
    Todo Updated
    ```

### API 5

#### Path: `/todos/:todoId/`

#### Method: `DELETE`

#### Description:

Deletes a todo from the todo table based on the todo ID

#### Response

```
Todo Deleted
```

<br/>

Use `npm install` to install the packages.

**Export the express instance using the default export syntax.**

**Use Common JS module syntax.**
