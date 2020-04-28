1. Create a database named `blog`.

```js
use blog;
```
2. Create a collection called 'articles'.
```js
db.createCollection("articles");
```
3. Insert multiple documents(at least 3) into articles. It should have fields
```js
db.articles.insert({"title": "HTML", "description": "Hyper Text Markup Language", "author": {"name": "xyz", "age": 21, "email": "email@email"}, "tag": ["webdevelopment", "node", "react"]});

db.articles.insert({"title": "CSS", "description": "Cascading Style Sheet", "author": {"name": "abc", "age": 25, "email": "email@email"}, "tag": ["css", "node", "react"]});

db.articles.insert({"title": "Node", "description": "Node Js is used for the backend", "author": {"name": "ghi", "age": 29, "email": "email@email"}, "tag": ["mongo", "node", "express"]});
```
4. Find all the articles using `db.COLLECTION_NAME.find()`
```js
db.articles.find();

//Output is: 
{ "_id" : ObjectId("5ea8600bba80c3c0ecb11403"), "title" : "HTML", "description" : "Hyper Text Markup Language", "author" : { "name" : "xyz", "age" : 21, "email" : "email@email" }, "tag" : [ "webdevelopment", "node", "react" ] }

{ "_id" : ObjectId("5ea8600bba80c3c0ecb11404"), "title" : "CSS", "description" : "Cascading Style Sheet", "author" : { "name" : "abc", "age" : 25, "email" : "email@email" }, "tag" : [ "css", "node", "react" ] }

{ "_id" : ObjectId("5ea8600bba80c3c0ecb11405"), "title" : "Node", "description" : "Node Js is used for the backend", "author" : { "name" : "ghi", "age" : 29, "email" : "email@email" }, "tag" : [ "mongo", "node", "express" ] }
```
5. Find a document using _id field.
```js
db.articles.find({_id: ObjectId("5ea8600bba80c3c0ecb11403")});
```
6. Find documents using title and author's name field.
```js
db.articles.find({}, {"title": "", "name": ""});
```
7. Find document using a specific tag.
```js
db.articles.find({"tag": "mongo"});
```
8. Update title of a document using its _id field.
```js
db.articles.update({_id: ObjectId("5ea8600bba80c3c0ecb11403")}, {$set : {"title": "Hyper TML"}});
```
9. Update a author's name using article's title.
```js
db.articles.update({"title":"Node"}, {$set: {"author": {"name":"ABCD"}}});

```
10. rename details field to description from articles collection. 
```js
db.articles.update({"title": "Node"}, {$set : {"description": "Backend Backend"}});
```
11. Add additional tag in a specific document.
```js
db.articles.update({"title": "Node"}, {$push: {tag: 'nodemon'}});
```
12. Update an article's tags using $set and without $set.

```js
db.articles.update({"title" : "Node"}, {$set : {"tag": 'changed tag'}});


db.articles.update({"title" : "Node"}, {"tag": 'changed tag'}});
```
  - Write the differences here ?

When we use {$set} it updates without changing the original data. When we update it without using {$set} we change the entire data for that field.

13. Increment an auhtor's age by 5.  

```js
db.articles.update({"title": "Node"}, {$inc: {"age": 5}});

```

14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
```js
db.articles.remove({_id: ObjectId("5ea8600bba80c3c0ecb11405")});

```
Use sample.js data for below queries.

1. Find all males who play cricket.
```js
db.users.find({gender: "Male"}, {sports: "cricket"});
```
2. Update user with extra golf field in sports array whose name is "Steve Ortega".
```js
db.users.update({name: "Steve Ortega"}, {$push:{sports: "golf"}});
```
3. Find all users who play either 'football' or 'cricket'.
```js
db.users.find({sports: "cricket"}, {sports: "football"});
```
4. Find all users whose name includes 'ri' in their name.
```js
db.users.find({name: /ri/i});
```