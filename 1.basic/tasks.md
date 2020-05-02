#### write commands for following mongodb opertaions

1. create a database named `sports`
// Answer here ..
```js
use sports
```
2. list all databases present in local mongod server.
// Answer here..
```js
show dbs

admin   0.000GB
config  0.000GB
local   0.000GB
```

3. create 3 collections named `cricket`, `football`, `TT` in sports database.
Answer: 
```js
db.createCollection('cricket')
db.createCollection('football')
db.createCollection('TT')
```

4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.
Answer: 
```js
db.cricket.insert({'name': 'user1', 'email': 'email1@email', 'age': 11}, {'name': 'user2', 'email': 'email2@email', 'age': 12}, {'name': 'user3', 'email': 'email3@email', 'age': 13});


db.football.insert({'name': 'user1', 'email': 'email1@email', 'age': 11}, {'name': 'user2', 'email': 'email2@email', 'age': 12}, {'name': 'user3', 'email': 'email3@email', 'age': 13});
WriteResult({ "nInserted" : 1 })


db.TT.insert({'name': 'user1', 'age': '11', 'email': 'email1@email'}, {'name': 'user2', 'age': '12', 'email': 'email2@email'}, {
'name': 'user3', 'age': '13', 'email': 'email3@email'})
```

5. list all collections in sports database.
Answer: 
```js
db.getCollectionNames()
[ "TT", "cricket", "football" ]
6. rename `TT` collection to `tennis`.
```
7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?

Answer: 

```js
db.createCollection('khokho', {capped: true, size: 1024, max: 3});

db.khokho.insert({'name': 'user1', 'age': '11', 'email': 'email1@email'});
db.khokho.insert( {'name': 'user2', 'age': '12', 'email': 'email2@email' });
db.khokho.insert( {'name': 'user3', 'age': '13', 'email': 'email3@email'});
 
 Output is has a size of 3 and the first entry is replaced and the latest entry is inserted in the end

```
8. check whether a collection is capped or not?
```js
db.khokho.isCapped()
true
```
9. remove all documents from `football` collection.
```js
db.football.remove({});
```
10. delete cricket collection completely.
```js
db.cricket.drop();
```
11. rename database sports to games
```js
db.copyDatabase("sports","games");
```
12. delete sports database. 
```js
db.sports.drop();
```
