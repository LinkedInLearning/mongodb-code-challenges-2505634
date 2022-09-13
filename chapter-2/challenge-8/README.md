# Challenge 2-8 - Custom query logic with `$where` and `$function`

## Challenge

Compose 2 queries, which separately use `$where` and `$expr` in a find) to run the following query in the customers collection, returning the customers name and favorite categories only

1. All customers whose favorite categories includes "sports"

Consider:

- The syntactic differences between defining a function using `$expr` vs an inline function as part of a `$where`
- How does the return value help to construct the output?
- Which does Mongo recommend and why?

### Hints

> Need a hand? Check out the official documentation: [$where](https://www.mongodb.com/docs/manual/reference/operator/query/where/) / [$function](https://www.mongodb.com/docs/manual/reference/operator/aggregation/function/)

## Solution

<details>
  <summary>Click to expand</summary>

### Using `$where

```javascript
db.customers.find(
  {
    $where: function () {
      return this.favoriteCategories && this.favoriteCategories.includes("sports");
    }
  },
  {_id: 0, name: 1, favoriteCategories: 1}
);
```

### Using an `$expr`

```javascript
db.customers.find(
  {
    $expr: {
      $function: {
        body: function (favoriteCategories) { return favoriteCategories && favoriteCategories.includes("sports") },
        args: ["$favoriteCategories"],
        lang: "js"
      }
    }
  },
  {_id: 0, name: 1, favoriteCategories: 1}
);
```

### Expected Output

```javascript
[
  { name: 'Gene', favoriteCategories: [ 'sports' ] },
  { name: 'Zach', favoriteCategories: [ 'sports' ] },
  { name: 'John', favoriteCategories: [ 'clothing', 'food', 'sports' ] },
  { name: 'Cathy', favoriteCategories: [ 'food', 'sports', 'clothing' ] }
]
```

</details>
