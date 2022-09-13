# Challenge 2-3 - Limiting and Sorting Results

## Challenge

Use find to run the following queries in the customers collection, returning only the customers name, email, and phone number

In each case, use chaining to `sort()` the names alphabetically (in both directions), and `limit()` the results to 5

1. Active Customers, sorted by name
1. The last 5 Customers who joined, sorted by active status and name

Hint: Sort takes an object indicating field names and sort direction. Limit simply needs a numeric value.

> Need a hand? Check out the official documentation: [Sorting](https://www.mongodb.com/docs/manual/reference/method/cursor.sort/) / [Limits](https://www.mongodb.com/docs/manual/reference/method/cursor.limit/). You might also want to read up on [Chaining Methods](https://www.geeksforgeeks.org/method-chaining-in-javascript/) in JavaScript

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.find(
  { active: true },
  { _id: 0, name: 1, email: 1, phone: 1 }
).sort({ name: 1 });

db.customers.find(
  {},
  { _id: 0, name: 1, email: 1, phone: 1 }
).sort({ customerSince: -1 }).limit(5);

```

### Expected Output

```javascript
[
  { name: 'John', email: 'john@example.com', phone: '206-555-1212' },
  {
    name: 'Josie',
    email: 'josie@exmple.com',
    phone: '555-1212'
  },
  { name: 'Zach', email: 'zach@example.com', phone: '206-555-3333' },
  { name: 'Allie', email: 'allie@example.com', phone: '206-555-4444' },
  { name: 'Gene', email: 'gene@exmple.com', phone: '555-1212' }
]
```

</details>
