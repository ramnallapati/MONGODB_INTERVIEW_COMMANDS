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