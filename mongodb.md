# MongoDB Cheatsheet

show the version of database server
```
    db.version()
```

returns some statistics about Mongodb
sever
```
db.stats()

list all the database in the MongoDB server
```
show dbs
```
switch to use the database specified
```
    use <dbName>
```
creates new collection in the database
```
db.createcollection("name)
```
list all collection under the specified
database
```
show collections
```

## Inserting document
Insert one document into our collection
```
    insertOne({...})
    syntax:
    db.<collectionName>.insertOne({})
    ```
    insertsMany([{}, {}...{}])
    syntax:
        db.<collectionName>.insertMany([{}, {}... {}])
        ```

## Finding document in collection
Return all the documents in the collection that matches the query.It will return an empty array if there is no document in the collection.If empty object ({}) is passed as query it will return all the document in the collection

## Query methods
Are methods helper methods of the find method.It needs to be chained after the find()method

sorts documents in either ascending or decending order
```
sort()
```

limits the returning documents to the number specified
```
limit()
```

skips the first number of items specified
```
skip()
```

counts the number of documents retured from a find result
```
count()
```
## Equality query
Match by field name and it’s exact value
```
Syntax:
    {<fieldName1> :  <value1>, <fieldName1> :  <value1>}

Example:
    {“name”:  “John Doe” }
    {“age”:  30}
    {“gender”: “male”,  “maritalStatus” : “single”}
```

## Query Operators
```
    $or				    $eq				$lt
    $and				$ne				$gt
    $gte				$lte			$in
    $nin				$regex
```

## Comparison operators
Operators add conditions that compares two or more values
```
Syntax:
    {<fieldName1>: {<operator1>: <value1>}, …}

Examples:
    {'age': {$gt : 25}}
    {'age': {$lt : 25}}
    {'favouriteFruit': {“$in”: [“apple”, “orange”]}}

```

This comparison operators require an ARRAY
```
Syntax:
    {<fieldName1>: { <operator1>:  [ <value1>,  <value2>] }, …}

Examples:
    {“eyeColor”: {“$in”: [“blue”, “brown”]}}
    {“favouriteFruit”: {“$nin”: [“apple”, “orange”]}}
```

## “and” operator
Logically combines multiple conditions. Resulting documents must much ALL conditions
```
Syntax
    { $and: [ { <condition1> }, { <condition2> } … ] }

Example
    { $and: [ {“gender” : “male”} , {“age” : 25 } ] }
```
NB
Explicit $and MUST be used if conditions contains same field or operator
