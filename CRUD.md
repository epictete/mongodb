# MongoDB CRUD Operations

1. [CREATE](#create)
1. [READ](#read)
1. [UPDATE](#update)
1. [DELETE](#delete)

## Manage DB and collection

### Show All Databases

```
show dbs
```

### Show Current Database

```
db
```

### Create Or Switch Database

```
use test
```

### Drop

```
db.dropDatabase()
```

### Create Collection

```
db.createCollection('météo')
```

### Show Collections

```
show collections
```

## CREATE

### Insert Row

```
db.météo.insert(
  {
    _id: 1,
    ville: "Bruxelles",
    haut: 27,
    bas: 13
  }
)
```

### Insert Multiple Rows

```
db.météo.insertMany([
  {
    _id: 1,
    ville: "Bruxelles",
    haut: 27,
    bas: 13
  },
  {
    _id: 2,
    ville: "Liège",
    haut: 25,
    bas: 15
  },
  {
    _id: 3,
    ville: "Namur",
    haut: 26,
    bas: 15
  },
  {
    _id: 4,
    ville: "Charleroi",
    haut: 25,
    bas: 12
  },
  {
    _id: 5,
    ville: "Bruges",
    haut: 28,
    bas: 16
  },
])
```

## READ

### Get All Rows

```
db.météo.find()
```

### Get All Rows Formatted

```
db.météo.find().pretty()
```

### Find Rows

```
db.météo.find(
  { haut: { $eq: 26  } }
)
```

### Sort Rows

##### ASC

```
db.météo.find().sort(
  { ville: 1 }
)
```

##### DESC

```
db.météo.find().sort(
  { ville: -1 }
)
```

### Count Rows

```
db.météo.find().count()
```

```
db.météo.find(
  { bas: { $lte: 14 } }
).count()
```

### Limit Rows

```
db.météo.find().limit(2)
```

### Chaining

```
db.météo.find().limit(2).sort(
  { ville: -1 }
)
```

### Foreach

```
db.météo.find().forEach(function(doc){
  print("Ville : " + doc.ville)
})
```

## UPDATE

### Update Row

```
db.météo.update(
  { ville: 'Charleroi' },
  {
    ville: 'Charleroi',
    haut: 27,
    bas: 14
  }
)
```

### Update Specific Field

```
db.météo.update(
  { ville: 'Bruxelles' },
  {
    $set: {
      haut: 25,
      bas: 11
    }
  }
)
```

### Increment Field (\$inc)

```
db.météo.update(
  { ville: 'Namur' },
  { $inc: { bas: 3 } }
)
```

## DELETE

### Delete Row

```
db.météo.remove(
  { ville: 'Namur' }
)
```

## Text Search

### Create New Collection

```
db.stores.insertMany(
   [
     { _id: 1, name: "Java Hut", description: "Coffee and cakes" },
     { _id: 2, name: "Burger Buns", description: "Gourmet hamburgers" },
     { _id: 3, name: "Coffee Shop", description: "Just coffee" },
     { _id: 4, name: "Clothes Clothes Clothes", description: "Discount clothing" },
     { _id: 5, name: "Java Shopping", description: "Indonesian goods" }
   ]
)
```

### Add Index

```
db.stores.createIndex(
  { name: "text", description: "text" }
)
```

### Text Search

```
db.stores.find(
  { $text: {$search: "Coffee" } }
)
```
