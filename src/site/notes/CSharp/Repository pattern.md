---
{"dg-publish":true,"permalink":"/c-sharp/repository-pattern/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Repository pattern

"An abstraction layer for your external data."

Repository Design Pattern in C# is used to create an abstraction layer between the data access layer and the business logic layer of your application.

The idea is that a *repository* should act like a *collection of objects in memory*. 

→ Therefore, it should not expose the semantics of your database. So you should not find methods like `Save()`.

## Example: 
A repository typically does at least five operations as follows:

1.  **Selecting all records from a table**
2.  **Selecting a single record based on its primary key**
3.  **Insert**
4.  **Update**
5.  **Delete**