
<div style="display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;">
    <img src="images/mongodb_image.png"
         width="500"
         height="700"
         alt="MongoDB Image">
</div>

<div style='margin:15px'>
<h1 style='text-align:center;color:red'>👁️ Mongodb Setup</h1>
<h3>Open the Mongodb Sheel </h3>
<h4>Create the Database ComapanyDB :</h4>
<code>
use ComapnaDB
</code>
<h4>Create collections using the above data from text files :</h4>
<code>
db.createCollection()
</code>
</div>

---

<h1 style='color:red;text-align:center;margin:15px'>📊 Basic Crud Operations</h1>

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

<h1 style='color:red;text-align:center;margin:15px'>🤖 Update Operations</h1>

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

<h1 style='color:red;text-align:center;margin:15px'> ⛏️ Array Operations</h1>

### 41. Find employees having the skill "Python".
```javascript
db.employees.find(
  {'skills':{$in:['Python']}}
)
```


### 42. Find employees having both Python and MongoDB skills.
```javascript
db.employees.find(
  {'skills':{$all:['Python','MongoDB']}}
)
```


### 43. Find employees having at least three skills.
```javascript
db.employees.find({
  $expr:{
    $gte:[{$size:"$skills"},3]
  }
})
```


### 44. Find employees whose first skill is Python.
```javascript
db.employees.find({'skills.0':'Python'})
```


### 45. Remove duplicate skills.
```javascript
db.employees.updateMany(
    {},
    [
        {
            $set: {
                skills: {
                    $setUnion: ["$skills", []]
                }
            }
        }
    ]
)
```


### 46. Add a new certification.
```javascript
db.employees.updateMany(
  {},
  {$addToSet:{
    'certification':'AWS Developer'
  }}
)
```

### 47. Remove all certifications.
```javascript
db.employees.updateMany(
  {},
  {$unset:{'certification':''}}
)
```


### 48. Find employees having TensorFlow or PyTorch.
```javascript
db.employees.find({
    skills: {
        $in: ["TensorFlow", "PyTorch"]
    }
})
```


### 49. Find employees without MongoDB skill.
```javascript
db.employees.find({'skills':{$nin:['MongoDB']}})
```


### 50. Find employees where any skill starts with "P".
```javascript
db.employees.find({'skills':{$regex:'^P'}})
```


### 51.Count employees with more than four skills.
```javascript
db.employees.countDocuments(
  {$expr:
  {
    $gt:[{$size:'$skills'},4]
  }}
)
```

### 52. Find employees whose last skill is SQL.
```javascript
db.employees.find({
  $expr:{
    $eq:[
      {$arrayElemAt:['$skills',-1]},
      'SQL'
    ]
  }
})
```


### 53.Push a project object into an array.
```javascript
db.employees.updateMany(
  {},
  {
    $push:
    {
      projects:
      {
        $each:
          [
            {
               project_id: 3,
                project_name: "Banking Application",
                technology: "Java",
                duration: 10,
            },
            {
              project_id:4,
              project_name:'AI Chatbot',
              technology:'TensorFlow',
              duration:5,
              status:'In Progress'
            }
          ]
      }
    }
  }
)
```

### 54. Remove a project object from an array.
```javascript
db.employees.updateMany(
  {},
  {
    $unset:{'projects':''}
  }
)
```

---

<h1 style='color:red;text-align:center;margin:15px'>🪢 Embedded Documents Data</h1>


### 55. Find employees living in Hyderabad using an embedded address document.
```javascript
db.emp_address.find({'address.city':'Hyderabad'})
```

### 56. Update the pincode inside the address.
```javascript
db.emp_address.updateMany(
  {},
  {
    $set: {
      "address.pincode": 523326
    }
  }
)
```

### 57. Find employees whose state is Telangana.
```javascript
db.emp_address.find({'address.state':'Telangana'})
```


### 58. Add a country field inside address.
```javascript
db.emp_address.updateMany(
  {},
  {
    $set:
    {
      'address.country':'India'
    }
  }
)
```


### 59. Remove address.pincode.
```javascript
db.emp_address.updateMany(
  {},
  {
    $unset:
    {
      'address.pincode':''
    }
  }
)
```


### 60. Update employee's emergency contact.
```javascript
db.employees.updateMany(
  {},
  {
    $set:
    {
      'emergency_contact':8309764967
    }
  }
)
```

### 61. Find employees whose manager's name is Murali.
```javascript
db.employees.find(
  {'manager_name':'Murali'}
)
```


### 62. Update nested project status.
```javascript
db.emp_address.updateMany(
  {},
  {
    $set:
    {
      'project_status':'Complete'
    }
  }
)
```



### 63. Display only address.city.
```javascript
db.emp_address.find(
  {},
  {
    _id:0,
    'address.city':1
  }
)
```
---

<h1 style='color:red;text-align:center;margin:15px'>🗝️ Query Operations</h1>

### 64. Find salaries greater than ₹50,000.
```javascript
db.employees.find({
  salary:
  {
    $gt:50000
  }
})
```


### 65. Find salaries less than ₹60,000.
```javascript
db.employees.find(
  {
    'salary':{$lt:60000}
  }
)
```


### 66. Find salaries between ₹40,000 and ₹70,000.
```javascript
db.employees.find(
  {
    salary:
    {
      $gt:40000,
      $lt:70000
    }
  }
)
```

### 67. Find salary not equal to ₹45,000.
```javascript
db.employees.find(
  {
    salary:
    {
      $ne:45000
    }
  }
)
```

### 68. Find employees in Hyderabad, Chennai, or Bangalore.
```javascript
db.emp_address.find(
  {
    'address.city':
    {
      $in:['Hyderabad','Chennai','Bengaluru']
    }
  }
)
```


### 69. Find employees not in Hyderabad.
```javascript
db.emp_address.find(
  {
    'address.city':
    {
      $ne:'Hyderabad'
    }
  }
)
```


### 70. Find employees whose names start with "R".
```javascript
db.employees.find(
  {
    name:
    {
      $regex:"^R"
    }
  }
)
```

```javascript
db.employees.find({name:/^R/})
```


### 71. Find employees whose names end with "a".
```javascript
db.employees.find(
  {
    name:/a$/
  }
)
```


### 72. Find employees whose names contain "an".
```javascript
db.employees.find(
  {
    name:/an/
  }
)
```


### 73. Find employees older than 25 and working in IT.
```javascript
db.employees.find(
  {
    age:
    {$lt:25},
    department:'IT'
  }
)
```

---

<h1 style='color:red;text-align:center;margin:15px'>🤝 Aggregation Functions</h1>

### 74. Calculate the total salary paid by the company.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:null,
        total_employees_salary:{$sum:"$salary"}
      }
    }
  ]
)
```


### 75. Find the average salary.
```javascript
db.employees.aggregate(
  [
    {
      $group:{
        _id:null,
        employees_average_salary:{$avg:"$salary"}
      }
    }
  ]
)
```

### 76. Find the highest salary.
```javascript
db.employees.aggregate(
  [
    {
      $group:{
        _id:null,
        employees_highest_salary:{$max:"$salary"}
      }
    }
  ]
)
```

### 77. Find the lowest salary
```javascript
db.employees.aggregate(
  [
    {
      $group:{
        _id:null,
        employees_lowest_salary:{$min:"$salary"}
      }
    }
  ]
)
```

### 78. Find department-wise average salary.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:"$department",
        dept_avg_salary:{$avg:"$salary"}
      }
    }
  ]
)
```

### 79. Find department-wise employee count.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:"$department",
        dept_emp_count:{$sum:1}
      }
    }
  ]
)
```


### 80. Find city-wise employee count.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:'$city',
        city_emp_count:{$sum:1}
      }
    }
  ]
)
```


### 81. Find the top five highest-paid employees.
```javascript
db.employees.aggregate(
  [
    {
      $sort:{salary:-1}
    },
    {
      $limit:3
    },
    {
      $project:{_id:0,name:1,salary:1,city:1}
    }
  ]
)
```


### 82. Find employees earning above the department average.
```javascript
db.employees.aggregate([
  {
    $setWindowFields: {
      partitionBy: "$department",
      output: {
        departmentAverage: {
          $avg: "$salary"
        }
      }
    }
  },
  {
    $match: {
      $expr: {
        $gt: ["$salary", "$departmentAverage"]
      }
    }
  },
  {
    $project: {
      _id: 0,
      name: 1,
      department: 1,
      salary: 1,
      departmentAverage: 1
    }
  }
])
```


### 83. Group employees by designation.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:"$designation"
      }
    }
  ]
)
```

### 84. Calculate total experience department-wise.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:'$department',
        department_total_experience:{$sum:"$experience"}
      }
    }
  ]
)
```

### 85. Find departments with more than five employees.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:'$department',
        emp_count:{'$sum':1}
      }
    },
    {
      $match:
      {
        emp_count:{$gt:5}
      }
    }
  ]
)
```

### 86. Sort departments by average salary.
```javascript
db.employees.aggregate(
  [
    {
      $group:
      {
        _id:'$department',
        dept_avg_salary:{$avg:"$salary"}
      }
    },
    {
      $sort:{dept_avg_salary:1}
    }
  ]
)
```


### 87. Find the second highest salary in a company
```javascript
db.employees.aggregate([
  {
    $sort: { salary: -1 }
  },
  {
    $limit: 2
  },
  {
    $skip: 1
  }
])
```

### 88. Display employee name and annual salary.
```javascript
db.employees.aggregate(
  [
    {
      $project:{
        _id:0,
        name:1,
        salary:1
      }
    }
  ]
)
```

---

