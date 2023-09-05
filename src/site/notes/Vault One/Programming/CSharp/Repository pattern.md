---
{"dg-publish":true,"permalink":"/vault-one/programming/c-sharp/repository-pattern/"}
---


# Repository pattern
[Check out](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/ff649690(v=pandp.10))

"An abstraction layer for your external data."
![RepositoryPattern.png](/img/user/Vault%20One/Illustrations/RepositoryPattern.png)

Repository Design Pattern in C# is used to create an abstraction layer between the data access layer and the business logic layer of your application.

The idea is that a *repository* should act like a *collection of objects in memory*. 

→ Therefore, it should not expose the semantics of your database. So you should not find methods like `Save()`. (Though I see it used in a lot of examples... 🤔 For example on [msdn](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application))

But if no save... then how [[Vault One/Programming/CSharp/Unit of work-pattern\|Unit of work-pattern]]? 

## Example: 
A repository typically does at least five operations as follows:

1.  **Selecting all records from a table**
2.  **Selecting a single record based on its primary key**
3.  **Insert**
4.  **Update**
5.  **Delete**

