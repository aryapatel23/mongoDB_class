**Task 1: Create a "CodingGita Students" database**

- Create a new MongoDB database called `CodingGita`.

**1: Create the database**
```js
use codinggita
```

**2:Add two collections:**
```js
db.createCollection("students");
```

```js
db.createCollection("courses");
```

**3:Insert sample data in students collection:**

```js
db.students.insertMany([
  { 
    "name": "Ridham",
    "rollNumber": 1,
    "department": "Computer Science",
    "year": 1,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Rijans",
    "rollNumber": 2,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Divy",
    "rollNumber": 3,
    "department": "Electrical Engineering",
    "year": 1,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);
``` 
**4:Insert sample data in course collection:**

```js
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Neel" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Patel" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Yadav" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Trivedi" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Parmar" 
  }
]);
```
---
---

**Task 2: Perform CRUD operations**

**4:Add a few more students and courses to the database:**

- Added in students. 

```js
db.students.insertOne({ 
    "name": "Jay",
    "rollNumber": 4,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  });
```

- Added in courses. 

```js
db.courses.insertOne({ 
    "courseCode": "CS104", 
    "courseName": "Figma", 
    "credits": 3, 
    "instructor": "Prof. Rushil" 
  });
```

**5:Query data based on:**

  - Department (e.g., "Computer Science").

  ```js
db.students.find({ "department": "Computer Science" });
```

  - Year (e.g., "2").

  ```js
db.students.find({ "year": 2 });
```
  - Courses enrolled (e.g., "CS101").

  ```js
db.students.find({ "coursesEnrolled": "CS101" });
```


**6:Update the courses for a specific student (e.g., adding a new course).**

- Update in students. 
```js
db.students.updateOne(
  { "name": "Divy" },
  { $push: { "coursesEnrolled": "CS102" } }
);
```

- Update in courses. 

```js
db.courses.updateOne(
  { "courseCode": "CS102" },
  { $set: { "instructor": "Prof. Gupta" } }
);
```

**7:Delete a student or course from the database.**

- Delete in Students. 

```js
db.students.deleteOne({ "name": "Divy" });
```

- Delete in Courses. 

```js
db.courses.deleteOne({ "courseCode": "CS102" });
```