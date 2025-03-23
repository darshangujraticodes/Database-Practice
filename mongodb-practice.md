# Best site to generate dummy json data is : Mockaroo

I have generated 2 dummy data Employee and Teachers to practice operation on large data sets :
[Mockaroo](https://www.mockaroo.com/) <br>

It has 2 crucial benefits <br>

1. Generate data in Customize format <br>
2. Generated Data can be exported in mulitple format eg. csv, json and many other formats. <br>

---

# How to run mongodb in linux after installation

=> mongodb start <br>

=> mongod --version <br>

=> sudo systemctl start mongod <br>

=> sudo systemctl status mongod <br>

=> mongosh <br> <br>

# How to run mongodb in windows after installation

=> mongod --version <br>

=> mongosh <br>

---

# MongoDB Commands

MongoDB uses camel case structure for query declaration.

short commands

command + tab => for autocomplete <br>
cls => clear mongodbshell screen <br>
mongodb uses camelcase code format.

## Database Operation

1. create database <br>
   syntax : use database_name;

```
use student
```

2. Display all database

```
show dbs
or
show databases;
```

Note : if you have created then too it wont show in show dbs untill and unless it has collection inside db.

3. Delete database

```
db.dropDatabase()
```

---

## Collection Operation

Note : Collection name and fields name inside collection are case sensitive <br>

1. create collection inside database (collection is similar to table)
   <br>
   syntax : db.createCollection('collection_name')

   ```
   db.createCollection('schools')
   ```

2. Delete collection form database; <br>
   syntax : db.collection_name.drop()

   ```
   db.schools.drop()
   ```

3. Display all collection inside database

   ```
   show collections;
   ```

---

## CRUD Operation

1. Insert value in collections it is of 2 types (insertOne() and insertMany())<br>

   ##### Insert operation

   - insertOne() <br>
     syntax :<br>
     db.collection-name.insertOne(
     {
     field1:value1,
     field2:value2,
     }
     )
     <br>
     <br>

     ```
     db.students.insertOne({
     rollno:5, name:'Rohan', stream:'science'
     })
     ```

   - insertMany() <br>
     syntax :<br>
     db.collection-name.insertMany([
     {
     field1:value1,
     field2:value2,
     },
     {
     field1:value1,
     field2:value2,
     },
     {
     field1:value1,
     field2:value2,
     },
     ] )
     <br>
     <br>

     ```
     db.students.insertMany([
     {rollno:2, name:'sahil',stream:'commerce'},
     {rollno:3, name:'vaibhav',stream:'arts'},
     {rollno:4, name:'Anurag',stream:'diploma', sports:'chess'},
     ])
     ```

- While inserting data in mongodb it has 2 operation methods <br>
  --> Ordered : It is default behaviour and line execution interpretor stops after encountering first error. <br>
  --> Unordered : It is behaviour which ee have to set by setting `{ orderend: false }` which will allow interpretor to move on even though if it encounter any error jump on next line.

---

2. Read Operation in MongoDB <br>

   ##### Read operation

   - Reading documents in MongoDB
   - Comparison Operators
   - Logical Operators
   - Cursors in MongoDB
   - Elements in Operators
     <br>

   Type1 : find() <br>
   It will fetch all elements of the collections <br>
   syntax : db.collection_name.find(); <br>

   ```
   db.students.find()
   ```

   Type2 : find({key:value}) <br>
   It will fetch required field value which will match the required condition of key value pair <br>
   syntax : db.collection_name.find({key:value}); <br>

   ```
   db.students.find({  'stream':'science'  })
   ```

   Type3 : findOne({key:value}) <br>
   It will fetch required field value which will match the required condition of key value pair but the only first match pair <br>
   syntax : db.collection_name.find({key:value}); <br>

   ```
   db.students.findOne({  'stream':'science'  })
   ```

   ##### Read operation using comparison operator

   We have multiple operator it define specific compairison operation <br>

   1. $eq = Equal <br>
   2. $neq = not equal <br>
   3. $lt = less than <br>
   4. $lte = less than equal too <br>
   5. $gt = greater than <br>
   6. $gte = greater than equal too <br>
   7. $in = in (it will display the data whose value is present the
   8. comparison array) <br>
   9. $nin = Not in (It will display the data whose value is not present the comparison array) <br>

   syntax : <br>
   db.collection_name.find({ 'field_name': {'$operator' : 'field_value' } }); <br>

   ```
   db.teachers.find( {  'joining_data' : { $eq : 2005 }  } );
   ```

   ```
   db.teachers.find( {  'joining_data' : { $in : [2005,2006,2007,2008] }  } );
   ```

   ##### Mongodb Cursors

   1. Cursors : Cursors in MongoDB is used to efficiently retrieve large result sets from Queries, providing control over the data retrieval process <br>

   2. MongoDB retrieve the query result in batches. <br>

   3. Default batch size is usually 101 documents. <br>

   4. It imporves the memory efficiency. <br>

   5. cursors are extending chain function which are applied on find(). <br>

   ##### Types of MondoDB cursor

   1. count() <br>
   2. limit() <br>
   3. skip() <br>
   4. sort() [1 => Ascending order , -1 => Descending order] <br>

   syntax : db.collection_name.find( { fieldname : { $operator : fieldvalue } } ).cursor(); <br>

   ```
   db.students.find({ rollno : {  $gt :  10  } }).count();
   db.students.find({ rollno : {  $gt :  10  } }).limit(3);
   db.students.find({ rollno : {  $gt :  10  } }).limit(3).skip(2);
   db.students.find({ rollno : {  $gt :  10  } }).limit(5).sort({ 'rollno': -1});

   ```

   ##### Mongodb Logical Operator

   There are multiple logical operator in mongodb

   1. $and
   2. $or
   3. $nor
   4. $not

   a. $and operator: <br>
   It execute only when both condition are true. <br>
   syntax : db.collection_name.find( $operator : [ (condition1), (condition2) ] ); <br>

   ```
   db.students.find( { $and : [ { rollno : {$gt  : 20} } , {'sports':'baseball' } ] } ).count();
   ```

   b. $or operator: <br>
   It execute only when any one condition is true. <br>
   syntax : db.collection_name.find( $operator : [(condition1), (condition2)] ); <br>

   ```
<<<<<<< HEAD
   db.students.find( { $or : [ { rollno : {$gt  : 150} } , {'sports':'baseball' } ] } ).count();
   ```

   a. $nor operator: <br>
   It execute only when both condition are true.
   syntax : db.collection_name.find( $operator : [] ); <br>
=======
   db.students.find( { $or : [ { rollno : {$gt  : 20} } , {'sports':'baseball' } ] } ).count();
   ```

   c. $nor operator: <br>
   It execute when none of the condition are true.<br>
   syntax : db.collection_name.find( $operator : [(condition1), (condition2)] ); <br>

   ```
   db.students.find( { $or : [ { rollno : {$gt  : 20} } , {'sports':'baseball' } ] } ).count();
   ```

   c. $not operator: <br>
   It has unique operation it invert the results eg. expression result is true invert into false. <br>
   syntax : db.collection_name.find( { fieldkey : { $operator : { condition } } } ); <br>

   ```
   db.students.find({  stream : { $not : { $eq : 'commerce' } }  });
   ```

---

3. Update Operation in MongoDB <br>

   ##### Update Operation

   - updateOne() <br>
     syntax :<br>
     db.collection_name.updateOne( (to fetch particular data from json) { field_key:field_value } , (set new data for required fields) {
     $set : {
     field_name : field_value,
     field_name : field_value,
     field_name : field_value
     }
     } );
     <br>

     ```
     db.students.updateOne({ rollno: 2 } , {  $set : {
         name : 'Mayank',
         sports : 'badminton',
         stream : 'science'
     }   }   );
     ```

---

4. Deleted Operation in MongoDB <br>

   ##### Delete Operation

   - deleteOne() <br>
     syntax :<br>
     db.collection_name.deleteOne( { field_key:field_value } );
     <br>

     ```
     db.students.deleteOne({ _id: ObjectId('66a4f9a6558c75c87a482f8f')  });
     ```

   - deleteMany() <br>
     syntax :<br>
     db.collection_name.deleteMany( { field_key:field_value } );
     <br>
     ```
     db.students.deleteMany({ stream: 'diploma'  });
     ```
>>>>>>> 0eaf1f572ce7b8893df98e478ac654fa88f2c48d

---

### Mongodb Import and Export

1. MongoImport <br>
   mongoimport is of 2 format syntax : <br>
   Note: import file size should be less than 16mb otherwise won't allow. <br>

   - Type 1 : When data is in json and not wrapped in array [ ] <br>
     syntax : mongoimport file_path_name\file_name.json -d database_name -c collection_name <br>

     ```
      mongoimport file_path\teachers.json -d school -c teachers;
     ```

   - Type 2 : When data is in json and wrapped in array [ ] <br>
     syntax : mongoimport file_path_name\file_name.json -d database_name -c collection_name --jsonArray <br>

     ```
      mongoimport file_path\teachers.json -d school -c teachers --jsonArray;
     ```

2. MongoExport <br>
   syntax : mongoexport -d database_name -c collection_name -o (denote output) file_store_path/file_name.json <br>

   ```
   mongoexport -d schools -c teachers -o teacher-export-data.json
   ```

---

### MongoDB Tutorial Reference

1. [MongoDB Course By Technical Thapa](https://youtu.be/rU9ZODw5yvU?si=y8GFQ6RplV6gv89e)
