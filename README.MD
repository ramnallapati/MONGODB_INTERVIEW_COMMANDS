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