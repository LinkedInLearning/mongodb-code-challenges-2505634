# Challenge 2-2 - Specifying the fields to return in a `find()`

## Challenge

Use find() to run the following queries in the customers collection:

1. Active Customers - return only name and phone
1. Customers whose name is “John” - return only name and email

### Bonus

- Exclude the _id field

### Hints

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/method/db.collection.find/#std-label-find-projection)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.find(
  { name: "John" },
  { _id: 0, name: 1, email: 1, phone: 1 }
)

db.customers.find({ active: true }, { name: 1, email: 1, _id:0 })
```

### Expected Output

```javascript
[
  { name: 'Gene', email: 'gene@exmple.com' },
  { name: 'Zach', email: 'zach@example.com' },
  { name: 'Cathy', email: 'cathy@example.com' },
  { name: 'Josie', email: 'josie@exmple.com' },
  { name: 'Allie', email: 'allie@example.com' },
  { name: 'Rosie', email: 'rosie@example.com' },
  { name: 'Luna', email: 'luna@example.com' }
]
```

</details>
