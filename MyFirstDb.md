# My First Mongo Database

1. Create a dataase called 'my_first_db'
```
test> use my_first_db
switched to db my_first_db
```

2. Create students collection
```
my_first_db> db.createCollection("students")
{ ok: 1 }
my_first_db> show collections
students
```