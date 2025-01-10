## **1. Create the Database and Collections**

**1: Create the database**
```js
use Assignment2
```

**2: Create the students collection**
```js
db.createCollection("students");
```

**3: Create the subjects collection**
```js
db.createCollection("subjects");
```

## **2. Insert Sample Data**

**1: Insert sample data into the students collection**

```js
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS", "MongoDB"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Circuit Theory", "Electrical Machines"]
  }
]);
```

**2: Insert sample data into the subjects collection**

```js
db.subjects.insertMany([
  { 
    "subjectName": "React",
    "topics": [
      "JSX", 
      "Components", 
      "State", 
      "Props", 
      "Hooks"
    ]
  },
  { 
    "subjectName": "NodeJS", 
    "topics": [
      "Modules", 
      "Express", 
      "File System", 
      "Asynchronous Programming"
    ]
  },
  { 
    "subjectName": "MongoDB", 
    "topics": [
      "Database Design", 
      "CRUD Operations", 
      "Aggregation", 
      "Indexes"
    ]
  }
]);
```

## **3. Querying Data**

**1: Query students based on department**

```js
db.students.find({ "department": "Computer Science" });
```

**2: Query students based on year**

```js
db.students.find({ "year": 2 });
```

**3: Query students by subject  enrollment**

```js
db.students.find({ "subjectsEnrolled": "React" });
```

**4: Query subjects with a specific topic**

```js
db.subjects.find({ "topics": "Hooks" });
```

## **4. Updating Data**

**1: Add a subject for a student**

```js
db.students.updateOne(
  { "name": "Mahir" },
  { $push: { "subjectsEnrolled": "MongoDB" } }
);
```

**2: Update a student's year**

```js
db.students.updateOne(
  { "name": "Arjun" },
  { $set: { "year": 4 } }
);
```

**3: Add a new topic to a subject**

```js
db.subjects.updateOne(
  { "subjectName": "React" },
  { $push: { "topics": "Advanced Hooks" } }
);
```

## **5. Deleting Data**

**1: Delete a student record**

```js
db.students.deleteOne({ "name": "Arjun" });
```

**2: Delete a subject from the subjects collection**

```js
db.subjects.deleteOne({ "subjectName": "MongoDB" });
```

## **6. More Practice Tasks**

#### **Task 1: Add multiple students**
Insert at least **5 students** into the `students` collection with unique roll numbers, names, departments, years, and subjects enrolled.

```js
db.students.insertMany([
  {
    "name": "Ridham",
    "rollNumber": 104,
    "department": "Information Technology",
    "year": 1,
    "subjectsEnrolled": ["Web Development", "Database Management"]
  },
  {
    "name": "Rijans",
    "rollNumber": 105,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  {
    "name": "Jay",
    "rollNumber": 106,
    "department": "Mechanical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Maths", "Fluid Mechanics"]
  },
  {
    "name": "Divy",
    "rollNumber": 107,
    "department": "Electrical Engineering",
    "year": 4,
    "subjectsEnrolled": ["Power Systems", "Environment Study"]
  },
  {
    "name": "Om",
    "rollNumber": 108,
    "department": "Computer Science",
    "year": 3,
    "subjectsEnrolled": ["React Native", "Database Management"]
  }
]);
```

#### **Task 2: Add multiple subjects**
Insert **4 subjects** into the `subjects` collection, each with 3 to 5 topics.

```js
db.subjects.insertMany([
  {
    "subjectName": "React Native",
    "topics": ["Components", "Navigation", "Hooks", "State Management"]
  },
  {
    "subjectName": "Thermodynamics",
    "topics": ["Laws of Thermodynamics", "Heat Transfer", "Entropy"]
  },
  {
    "subjectName": "Database Management",
    "topics": ["SQL Basics", "Normalization", "Transactions"]
  },
  {
    "subjectName": "Power Systems",
    "topics": ["Transmission Lines", "Load Flow Analysis", "Protection Devices"]
  }
]);
```

#### **Task 3: Query students based on subject enrollment**
Query the `students` collection to find all students who are enrolled in **NodeJS**.

```js
db.students.find({ "subjectsEnrolled": "NodeJS" });
```

#### **Task 4: Add a new topic to a subject**
Add a new topic to the **NodeJS** subject.


```js
db.subjects.updateOne(
  { "subjectName": "NodeJS" },
  { $push: { "topics": "Performance Optimization" } }
);
```

#### **Task 5: Query subjects with multiple topics**
Query the `subjects` collection to find subjects that contain **at least 4 topics**.

```js
db.subjects.find({ "topics.3": { $exists: true } });
```

#### **Task 6: Update student enrollment**
Add the subject **"React Native"** to **Jenil's** subjects.

```js
db.students.updateOne(
  { "name": "Jenil" },
  { $push: { "subjectsEnrolled": "React Native" } }
);
```

#### **Task 7: Query all students**
Query all students in the database and print out their names and enrolled subjects.

```js
db.students.find({}, { "name": 1, "subjectsEnrolled": 1, "_id": 0 });
```

#### **Task 8: Update multiple students' year**
Update the year for all students in the **Computer Science** department to year 3.

```js
db.students.updateMany(
  { "department": "Computer Science" },
  { $set: { "year": 3 } }
);
```

#### **Task 9: Add new topics to multiple subjects**
Add new topics to **React**, **NodeJS**, and **MongoDB** subjects. Ensure each subject gets at least **one** new topic.

```js
db.subjects.updateOne(
  { "subjectName": "React" },
  { $push: { "topics": "Context API" } }
);

db.subjects.updateOne(
  { "subjectName": "NodeJS" },
  { $push: { "topics": "Microservices" } }
);

db.subjects.updateOne(
  { "subjectName": "MongoDB" },
  { $push: { "topics": "Sharding" } }
);
```

#### **Task 10: Remove a topic from a subject**
Remove the topic **"Express"** from the **NodeJS** subject.

```js
db.subjects.updateOne(
  { "subjectName": "NodeJS" },
  { $pull: { "topics": "Express" } }
);
```

#### **Task 11: Query all students in a specific year**
Query and return all students in **year 2** or **year 3**.

```js
db.students.find({ "year": { $in: [2, 3] } });
```

#### **Task 12: Delete a student by roll number**
Delete a student from the database using their **roll number**.

```js
db.students.deleteOne({ "rollNumber": 106 });
```

#### **Task 13: Delete all students from a department**
Delete all students who belong to the **Electrical Engineering** department.

```js
db.students.deleteMany({ "department": "Electrical Engineering" });
```

#### **Task 14: Retrieve all topics for a subject**
Query the **MongoDB** subject and retrieve all topics listed for it.

```js
db.subjects.find(
  { "subjectName": "MongoDB" },
  { "topics": 1, "_id": 0 }
);
```

#### **Task 15: Count the number of subjects in which a student is enrolled**
Write a query that returns the number of subjects each student is enrolled in.

```js
db.students.find({}, { name: 1, subjectsEnrolled: 1 });
```