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