# ActiveRecord CRUD Intro

## Objectives


1. Understand CRUD.
2. Get familiar with how to use CRUD.

## What is CRUD?

CRUD is an acronym for the four verbs we use to operate on data: **C**reate, **R**ead, **U**pdate and **D**elete. Active Record automatically creates methods to allow an application to read and manipulate data stored within its tables.

### Create

To create new objects, we can either use the `new` or `create` method. 

The `new` method will create a new object without any attributes.

```ruby
cat = Cat.new
```
To add attributes to our cat instance we need to write:

```ruby
cat = Cat.new
cat.name = "Maru"
cat.age = 3
```
The new method instantiates an object without saving it in the database. To persist the data we need to save it.

```ruby
cat = Cat.new
cat.name = "Maru"
cat.age = 3
cat.save
```

The `create` Method will create and save the object to the database.

```ruby
cat = Cat.create(name: "Maru", age: 3)
```

### Read

Active Record provides us with different methods to retrieve data from the database.

To get a collection of all cats, we will use the `all` method.

```ruby
cats = Cat.all
```

If you only want to get the first entry in your database.

```ruby
cat = Cat.first
```

When you are looking for a specific attribute, but keep in mind this will return the first entry that it finds in the database.

```ruby
maru = Cat.find_by(name: "Maru")
```

Like SQL we can also use the `where` method in activerecord.

```ruby
cat = Cat.where('age > 2')
```

### Update

### Delete