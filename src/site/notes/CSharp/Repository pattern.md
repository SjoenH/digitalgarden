---
{"dg-publish":true,"permalink":"/c-sharp/repository-pattern/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Repository pattern

`IRepository` - Gives us methods like 
- `Add()`
- `Remove()`
- `Get(id)`
- `Find(predicate)`

A repository should act like a collection of objects in memory. 
→ Therefore, it should not expose the semantics of your database. So you should not find methods like `Update()` and `Save()`.
