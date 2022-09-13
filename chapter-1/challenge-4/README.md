# Challenge 1-4 - Insert Multiple Documents using Loops

## Challenge

1. Create an array of at least 5 customer documents to insert into the customers collection.
1. Use the `insertMany()` method from within a `for()`, `while()`, or `forEach()` loop in `mongosh` to import these documents into your customers collection from this array
   - Trap any errors that arise from faulty data.

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertOne/)

## Solution

<details>
  <summary>Click to expand</summary>

### Insert a record, with error trapping

```javascript
customers = [
  {
    name: "Rosie",
    email: "rosie@example.com",
    phone: "206-555-5555",
    active: true,
    customerSince: ISODate("2021-09-12"),
    favoriteCategories: ["food"],
    orders: [],
    addresses: {
      shipping: {
        address: "123 Bark Ave",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      }
    }
  },
  {
    name: "Luna",
    email: "lunax@example.com",
    phone: "206-555-6666",
    active: true,
    customerSince: ISODate("2021-09-12"),
    orders: [],
    addresses: {
      shipping: {
        address: "124 Bark Ave",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      }
    }
  },
]

// No error checking:
customers.forEach(customer => db.customers.insertOne(customer))

// Better - trap any errors
let failures = [];

customers.forEach(customer => {

  try {
    result = db.customers.insertOne(customer);
    // stock or custom output
    print(result);
  } catch (e) {
    failures.push(customer);
    print(e);
  }

})

print(failures);

```

### Expected Output

```javascript
{
  acknowledged: true,
  insertedId: ObjectId("63190f8cc8041424d73a88a2")
}
{
  acknowledged: true,
  insertedId: ObjectId("63190f8cc8041424d73a88a3")
}
```

</details>
