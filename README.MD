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

###