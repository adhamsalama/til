https://www.mongodb.com/docs/manual/reference/operator/update/positional/

The positional operator "$" only updates objects in array that match the filter

For example:

```js
{
  _id: 4,
  grades: [
     { grade: 80, mean: 75, std: 8 },
     { grade: 85, mean: 90, std: 5 },
     { grade: 85, mean: 85, std: 8 }
  ]
}
```

Doing this:

```js
db.students.updateOne(
   { _id: 4, "grades.grade": 85 },
   { $set: { "grades.$.std" : 6 } }
)
```

updates only the first object that has a grade of 85.

So the after the updated:

```js
{
   "_id" : 4,
   "grades" : [
      { "grade" : 80, "mean" : 75, "std" : 8 },
      { "grade" : 85, "mean" : 90, "std" : 6 },
      { "grade" : 85, "mean" : 85, "std" : 8 }
   ]
}
```


If ```"grades.grade": 85``` was not specified, MongoDB would throw an error:


```MongoServerError: The positional operator did not find the match needed from the query.```
