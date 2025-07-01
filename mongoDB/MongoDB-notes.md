# Mongo DB Course Notes Course Refered : Engineering digest Youtube Course

### What is MongoDB ?

1. It is database server
2. It combination of 2 word mongo and db, mongo means huge and db means database. Database which store large amoun t of data
3. Highly scalable
4. documents consist of data in json format.
5. sql has table and table stored multiple data in rows format similarly nosql has collections and stored document on curly braces json format.
6. It has less relations
7. data is stored together
8. doument data is stored in "BJSON" Binary JSON convert data into binary to make it machine understandable and fast processing.

eg. collections employee

```
[
  {
    "name" : "Harsh Shah",
    "age" : "27",
    "dept" : "development",
    "salary" : "800000 lpa"
    "identity" : {
      "aadhar" : "242202524987",
      "pan": "GGOKL0874F",
    },
    "type" : "fresher",
  },
  {
    "name" : "Darsh Shah",
    "age" : "27",
    "dept" : "development",
    "salary" : "1500000 lpa"
    "identity" : {
      "aadhar" : "243302524877",
      "pan": "MMOKL0834F",
    },
    "type" : "experience",
    "exp_year" : "2",
    "previous" : ["amazon" , "google"]
  },
]

```

|    Database    |                   MySQL                   |           MongoDB (NoSQL DB)           |
| :------------: | :---------------------------------------: | :------------------------------------: |
|    DB Type     |               Relational DB               |           Document Oriented            |
| data structure |          Table with row & column          |             JSON Structure             |
|     Schema     |               fixed schema                |     flexible schema ( Schemaless)      |
|  Scalability   |             Vertical Scaling              |           Horizontal Scaling           |
|  Transactions  |         Support ACID transactions         |       Support ACID transactions        |
|  Performance   | Use for structured data & complex queries | Use for unstructured & large datasets  |
|   Use Cases    |        Banking ,Ecom ,ERP ,CRM etc        | Big data, data analytics, social media |
|  DB structure  |           database, table, rows           |    database, collections, documents    |

<br>

> [!NOTE]
>
> - Vertical Scaling : (Adding more CPU / RAM to single server)
> - Horizontal Scaling : (Adding more server for distributed storage)
> - ACID stands for Atomicity, Consistency, Isolation, and Durability—a set of properties that ensure reliable database transactions. These properties are crucial for maintaining data integrity in databases, especially in relational systems like MySQL.

### MongoDB Commands

**Database Operation Commands**

1. Create New Database <br>
   `syntax : use database_name` <br>
   example : `use college` <br>
   If it does not have that database then it will create and use.<br> <br>

2. Delete Database <br>
   step 1 : Go into that database which u want to delete <br>
   step 2 : Execute command `db.dropDatabase()`<br><br>

**Collection Operation Commands**

1. Create Collections <br>
   `syntax : db.createCollection("<collection_name>", { options })` <br>
   example : `db.createCollection('students')` <br>

2. Delete Collections <br>
   `syntax : db.<collection_name>.drop()` <br>
   example : `db.students.drop()`<br>

3. Show Collections <br>
   `syntax : show collections` <br>
   example : `show collections`<br> <br>

**Docmuments Operation** <br>

1. CREATE | Insert Data in Collections <br>
   `syntax : db.<collection_name>.insertOne({ query })` <br>
   `syntax : db.<collection_name>.insertMany([{ query }, { query } , { query }])` <br>
   It is of 2 types : insertMany() | insertOne() <br>
   example : `db.students.insertOne({name: "Rohit", roll_no:1, stream:"Science"})` <br>
   example : `db.students.insertMany( [ { rollno:101 , name: 'deepak'  } , { rollno:102 , name: 'aniket'   } , {   rollno:103 , name: 'sahil'   }   ] , { ordered : false }  )` <br>
   note while inserting multiple data insert all json query in list [] <br>
   To remove synchronize behavior : if this options `{ ordered : false }` is added as options it will break synchronize behaviour of mongodb and will execute other query by jumping to next if found any error in any query while executing it. <br> <br>

2. READ | Display Collection data <br>
   `syntax : db.<collection_name>.find()/find({})` : It return all document inside collections. <br>
   `syntax : db.<collection_name>.findOne()` : It returns only one conditional match document. <br>
   `syntax : db.<collection_name>.find({ key:value })` : It returns and display all conditional match document <br>
   `syntax : db.<collection_name>.find().count()` : display the total count of conditional match documents <br>
   `syntax : db.<collection_name>.find({  'idCards.hasPanCard' : true })` : dot operator use to match nested object conditions and wrap it in '' single inverted comma
   `db.students.find({}).forEach((x) => {printjson(x)})` -> forEach loop on find() <br>
   `db.students.find({ rollno : { $gte : 5 , $lte : 25 } }).count()` -> conditional operator <br>
   `db.students.find({ rollno : { $gt : 5 , $lt : 30 }  }).toArray()` -> return json doc into array values <br>
   `db.students.find({} , {name : 1 , _id : 0} )` -> return array of name data only | options it will display specific data just like here we are fetching only name and all set to 0
   <br><br>

3. UPDATE | Update data in Collection <br>
   `syntax : db.<collection_name>.updateOne( { condition } , { $set : { query } });` <br>
   `syntax : db.<collection_name>.updateMany( { condition } , { $set : { query } });` <br>
   To update only single values in collection <br>
   It is also called nested document (creating doc inside doc) <br>
   Nested Doc has limit of 100 and Max Memory size to store nested doc is 16mb <br>
   Here we are creating idCard nested doc inside student main doc with `$set` <br>
   example : `db.students.updateOne({name: "Ram"},{ $set: {  idCard : { hasDomicile: true, hasAadharCard : true   } } })` <br>

To update all values in collection <br>
example : `db.students.updateMany({},{ $set: {  idCard : { hasDomicile: false, hasAadharCard : true   } } })` -> add nested doc inside main doc <br>
example : `db.students.updateMany({},{ $set: {  hobbies: ['Anime', 'reading books','exploring new place']  } })` -> adding list inside main doc <br>
example : `db.students.updateMany({ rollno : { $gte : 50 } },{ $set: {  hobbies: ['Anime', 'reading books','exploring new place']  } })` -> adding list inside main doc <br>
example : ` db.students.updateMany({ rollno : {$gt : 80} } , {  $set : { isEligible : true }  })` -> will update all rollno greater than 80 with isEligible true

- DELETE | Delete data in Collection <br>
  `syntax : deleteOne(  { query } , options) | deleteMany( { query } , options)` <br>
  example : `db.students.deleteOne({ name: 'ajay' })` -> It help to delete single value in collections <br>
  example : `db.students.deleteMany({ rollno : { $gte : 3 , $lte : 5 } } )` -> it help to delete multiple value in collections
  example : `db.students.deleteMany({} )` -> it will delete all records in collections

### MongoDB Datatypes

- Text - String
- Boolean - True or False
- Number
  - Integer (32 bit)
  - NumberLong (64 bit)
  - NumberDecimal (decimal)
- objectId
- ISODate - Date
- TimeStamp - milliseconds
- Array - grouping similar type of data in list
- Embedded Document / Nested Document -

example :
`db.softmo.insertOne( { name: 'softmo', teamMember : 45, isRegistered : true , funding : 46464546465464456, foundingDate : new Date(), employee : [ { name: 'darshan' , dept : "Developer" } , { name: 'Roshni' , dept : "HR" } ] } )`

Output

```
[
  {
    _id: ObjectId('67b865c91ea91b1133c4e4a2'),
    name: 'softmo',
    teamMember: 45,
    isRegistered: true,
    funding: 46464546465464456,
    foundingDate: ISODate('2025-02-21T11:38:49.560Z'),
    employee: [
      { name: 'darshan', dept: 'Developer' },
      { name: 'Roshni', dept: 'HR' }
    ]
  }
]

```

Can Also be check using typeof to find data type of key value in json

### MongoDB Schema Validation
