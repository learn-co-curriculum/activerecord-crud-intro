# ActiveRecord CRUD Intro

## Objectives


1. Understand CRUD - Create, Read, Update, and Delete.
2. Get familiar with how to use ActiveRecord methods for Crud.

## What is CRUD?

CRUD is an acronym for the four verbs we use to operate on data: **C**reate, **R**ead, **U**pdate and **D**elete. Active Record automatically creates methods to allow an application to read and manipulate data stored within its tables.

### Create

To create new objects, we can either use the `new` or `create` method. 

The `new` method instantiates a new object in memory. In this case, we instantiate it without any attributes.

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

The `create` Method will create an object with its attributes and save it to the database. We pass in the attributes using hash syntax. The key is the name of the column we're updating and the value is what we're changing it to.

```ruby
cat = Cat.create(name: "Maru", age: 3)
```

### Read

Active Record provides us with different methods to retrieve data from the database.

To get a collection of all cats, we will use the `all` method. 

```ruby
cats = Cat.all
```
This returns an array of every cat from our database.

If you only want to get the first entry in your database, we will use the `first` method.

```ruby
cat = Cat.first
```

When you are looking for a specific attribute you can use the `find_by` method, but keep in mind this will only return the first entry that it finds.

```ruby
maru = Cat.find_by(name: "Maru")
```
This returns the first cat in that database where the name is "Maru".

Like SQL we can also use the `where` method in ActiveRecord.

```ruby
cat = Cat.where('age > 2')
```
This returns an array of all cats where the 'age' value is greater than 2.

### Update

After retrieving an ActiveRecord object, we can also modify its attributes. 

```ruby
hannah = Cat.find_by(name: 'Hana') 
hannah.name = "Hannah"
hannah.save
```
Notice that after changing the attribute we also have to persist the new name in the database by using the save method. Or we could use the `update` method that comes with the ActiveRecord API.

```ruby
hannah = Cat.find_by(name: 'Hana') 
hannah.update(name: "Hannah")
```

### Delete

Likewise, after retrieving an ActiveRecord object, the object can be destroyed.

```ruby
hannah = Cat.find_by(name: 'Hannah') 
hannah.destroy
```

If we want to delete all the cats from out database, we can use the ActiveRecord's class method `.destory_all`.

```ruby
Cat.destroy_all
```
This will delete each row in our table.
<p data-visibility='hidden'>View <a href='https://learn.co/lessons/activerecord-crud-intro' title='ActiveRecord CRUD Intro'>ActiveRecord CRUD Intro</a> on Learn.co and start learning to code for free.</p>
