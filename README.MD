### 1. Display all employees.
```bash
db.employees.find({})
```

### 2. Display only employee names.
```bash
db.employees.find(
  {},{_id:0,name:1}
)
```


### 3. Display employees whose salary is greater than 50000
```bash
db.employees.find(
  {'salary':{$gt:50000}}
)
```



### 4.Find employees whose salary is between ₹40,000 and ₹80,000.
```bash
db.employees.find(
  {'salary':
  {
    $gte:40000,
    $lte:80000
  }
  })
```


### 5. Find employees from Hyderabad.
```bash
db.employees.find({'city':'Hyderabad'})
```