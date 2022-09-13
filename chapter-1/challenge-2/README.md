# Challenge 1-2 - Insert a Document

1. Create an object representing a customer as we have previously modeled.
1. Use the `insertOne()` method from within `mongosh`  to import this document object into your customers collection.
   - Capture the result of the operation in a variable and then print it.
   - Trap any errors and report

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertOne/)

## Solution

<details>
  <summary>Click to expand</summary>

### Insert a record, with error trapping

```javascript
try {
  newCustomer = db.customers.insertOne({
    name: "John",
    email: "john@example.com",
    phone: "206-555-1212",
    active: true,
    customerSince: ISODate("2022-08-30"),
    favoriteCategories: ["clothing"],
    orders: [],
    addresses: {
      billing: {
        address: "123 Main St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      },
      shipping: {
        address: "123 Pine St",
        city: "Somewhere",
        state: "NJ",
        zip: "12345"
      }
    }
  });
  print("Record Inserted");
} catch (e) {
  print("Something went wrong", e);
}
```

### Prove It

```javascript
print(db.customers.find({ _id: newCustomer.insertedId }));
```

</details>
