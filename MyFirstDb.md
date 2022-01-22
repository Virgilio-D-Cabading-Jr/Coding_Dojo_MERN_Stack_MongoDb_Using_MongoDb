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

3. Create 5 students
```
db.students.insertOne({name: "Val", home_state: "Texas", lucky_number: 18, birthday: {month: 10, day: 12, year: 1978}})

db.students.insertOne({name: "Chris", home_state: "California", lucky_number: 7, birthday: {month: 12, day: 25, year: 1976}})

db.students.insertOne({name: "Adam", home_state: "Idaho", lucky_number: 2, birthday: {month: 1, day: 1, year: 1979}})

db.students.insertOne({name: "Krystal", home_state: "Texas", lucky_number: 8, birthday: {month: 2, day: 14, year: 1984}})

db.students.insertOne({name: "Leo", home_state: "California", lucky_number: 2, birthday: {month: 7, day: 4, year: 1994}})
```

4. Get all students
```
db.students.find()
```
5. Get all students who re from California
```
db.students.find({home_state:"California"})
```
6. Get all students whose lucky number is greater than 3
```
db.students.find({ lucky_number: {$gt: 3 } })
```
7. Get all student whose lucky number is less than or equal to 10
```
db.students.find({ lucky_number: { $lte: 10 } })
```
8. Get all students whose lucky number is between 1 and 9
```
db.students.find({ lucky_number: { $gte:1 , $lte:9 }})
```
9. Add a field to each student collection called 'interests' that is an ARRAY.  it should contain the following entries: 'coding', 'brunch', 'MongoDB'.  Do this in one operation
```
db.students.updateMany({}, {$set: {interests: ["coding","brunch","MongoDB"]}})
```
10. Add some unique interests for each particular student into each of their interest arrays
```
db.students.updateOne({name: "Val"}, {$push: {interests: "football"}})
db.students.updateOne({name: "Chris"}, {$addToSet: {interests: "tech"}})
db.students.updateOne({name: "Adam"}, {$addToSet: {interests: "black belt"}})
db.students.updateOne({name: "Krystal"}, {$addToSet: {interests: "money"}})
db.students.updateOne({name: "Leo"}, {$addToSet: {interests: "new car"}})
```