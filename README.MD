### 1. Display all employees.
```javascript
db.employees.find({})
```

### 2. Display only employee names.
```javascript
db.employees.find(
  {},{_id:0,name:1}
)
```


### 3. Display employees whose salary is greater than 50000
```javascript
db.employees.find(
  {'salary':{$gt:50000}}
)
```



### 4.Find employees whose salary is between ₹40,000 and ₹80,000.
```javascript
db.employees.find(
  {'salary':
  {
    $gte:40000,
    $lte:80000
  }
  })
```


### 5. Find employees from Hyderabad.
```javascript
db.employees.find({'city':'Hyderabad'})
```


### 6. Find employees whose age is greater than 25
```javascript
db.employees.find({'age':{$gt:25}})
```

### 7. Display only the first five employees.
```javascript
db.employees.find().limit(5)
```


### 8. Skip the first three employees and display the rest.
```javascript
db.employees.find().skip(3)
```

### 9.Sort employees by salary in ascending order.
```javascript
db.employees.find().sort({'salary':1})
```


### 10. Sort employees by age in descending order.
```javascript
db.employees.find().sort({'salary':-1})
```

---

### 11. Find one employee named "Rama Rao".
```javascript
db.employees.find({'name':'Rama Rao'})
```


### 12. Count employees working in the IT department.
```javascript
db.employees.countDocuments({'department':'IT'})
```


### 13. Find employees whose department is IT or HR.
```javascript
db.employees.find({
  department:{
    $in:['IT','HR']
  }
})
```


### 14. Find employees whose department is neither IT nor HR.
```javascript
db.employees.find({
  department:{
    $nin:['IT','HR']
  }
})
```

### 15. Find employees whose salary is not equal to ₹60,000.
```javascript
db.employees.find({'salary':{$ne:60000}})
```


### 16. Find employees whose email exists.
```javascript
db.employees.find({email:{$exists:true}})
```


### 17. Find inactive employees.
```bash
db.employees.find({"active":false})
```

### 18. Find employees whose phone number does not exist.
```javascript
db.employees.find({
    phone: { $exists: false }
})
```

### 19. Display employees without showing _id.
```javascript
db.employees.find({},{_id:0})
```


### 20. Delete an employee whose emp_id is 105.
```javascript
db.employees.deleteOne({"emp_id":105})
```

---


### 21. Increase everyone's salary by ₹5,000.
```javascript
db.employees.updateMany(
  {},
  {$inc:{'salary':5000}}
)
```


### 22. Increase only IT employees' salary by 10%.
```javascript
db.employees.updateMany(
  {'department':'IT'},
  {$mul:{'salary':1.10}}
)
```


### 23. Change "Software Engineer" to "Senior Software Engineer".
```javascript
db.employees.updateMany(
  {'designation':'Software Engineer'},
  {$set:{'designation':'Senior Software Engineer'}}
)
```

### 24. Update the city of employee 101 to Chennai.
```javascript
db.employees.updateOne(
  {'emp_id':101},
  {$set:{'city':'Chennai'}}
)
```

### 25. Rename the field phone to mobile.
```javascript
db.employees.updateMany(
  {},
  {$rename:{'phone':'mobile'}}
)
```


### 26. Remove the email field from all HR employees.
```javascript
db.employees.updateMany(
  {'department':'HR'},
  {$unset:{'email':''}}
)
```


### 27. Add a bonus field with value 10,000.
```javascript
db.employees.updateMany(
  {},
  {$set:{'bonus':10000}}
)
```

### 28. Add a joining year field.
```javascript
db.employees.updateMany(
  {},
  {$set:{'Joining_year':2026}}
)
```


### 29. Change active status to false for employees with experience less than 2 years.
```javascript
db.employees.updateMany(
  {'experience':{$lt:2}},
  {$set:{active:false}}
)
```

### 30. Replace the complete document of employee 102.
```javascript
db.employees.replaceOne(
  {'emp_id':102},
  {
    emp_id: 102,
    name: "Priya Sharma",
    age: 27,
    gender: "Female",
    department: "HR",
    designation: "HR Executive",
    salary: 55000,
    experience: 4,
    email: "priya@gmail.com",
    phone: "9123456789",
    city: "Bengaluru",
    joining_date: new Date("2022-08-15"),
    skills: ["Recruitment", "Employee Relations", "MS Excel"],
    manager_id: 202,
    active: true
}
)
```

--- 

### 31. Add a new skill to employee 101.
```javascript
db.employees.updateOne(
    { emp_id: 101 },
    {
        $push: {
            skills: "Java"
        }
    }
)
```


### 32. Remove the skill "SQL" from employee 101.
```javascript
db.employees.updateOne(
  {'emp_id':101},
  {$pull:{'skills':'SQL'}}
)
```


### 33. Add multiple skills at once.to all the employees
```javascript
db.employees.updateMany(
  {},
  {$push:{'skills':{$each:['Communication','Punctuality','Time Management']}}}
)
```


### 34. Remove the last skill from every employee.
```javascript
db.employees.updateMany(
  {},
  {$pop:{'skills':1}}
)
```


### 35. Add skill only if it doesn't already exist.
```javascript
db.employees.updateMany(
  {},
  {$addToSet:{'skills':'AI'}}
)
```


### 36. Update nested address.city from in Telangana. Hyderabad to Vishakapatnam
```javascript
db.emp_address.updateMany(
  {'address.state':'Telangana'},
  {$set:{'address.city':'Vishakapatanam'}}
)
```


### 37. Update salary only if it is below ₹40,000. Increasing 5 percentage.
```javascript
db.employees.updateMany(
  {'salary':{$lt:40000}},
  {$mul:{'salary':1.05}}
)
```


### 38. Increase the Salary to every employee 20 percentage.
```javascript
db.employees.updateMany(
  {},
  {$mul:{'salary':1.20}}
)
```

### 39. Change current date using $currentDate.
```javascript
db.employees.updateMany(
  {},
  {$currentDate:{'joining_date':true}}
)
```


### 40. Add a Field Latest updated
```javascript
db.emp_address.updateMany(
  {},
  {
    $currentDate: {
      latest_update: true
    }
  }
)
```

---