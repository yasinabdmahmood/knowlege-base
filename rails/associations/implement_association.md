# How to implement associations

## One to many relationship 
Assume that we have two table users table and records table , user has many records and record belongs to use

### Step 1
Generate empty migration

```code
rails generate migration AddUserRefToRecord
```
you will get a file in db/migrate directory that looks like following 

```ruby
class AddUserRefToRecord < ActiveRecord::Migration[7.0]
  def change
  end
end
```

### Step 2

Add the following line inside the migration file
```ruby
class AddUserRefToRecord < ActiveRecord::Migration[7.0]
  def change
  + add_reference :records, :author, null: false, foreign_key:{to_table: :users}
  end
end
```
the above code adds column author_id to records table that acts as foriegn key to reference to the users table
#### Note
it is convention that the table with foriegn key is given a name of the referenced table with _id suffex <br>
for exapmle user_id is the default name of the foriegn key column in records table but in above case we wish to name the column as 
author_id and go agains the conventions that is why we added
```ruby
  + add_reference :records, :author, null: false, foreign_key:{to_table: :users}
```

instead of 
```ruby
  + add_reference :records, :author, null: false, foreign_key:true
```

### Step 2
Modify the User model code
```ruby
class User < ApplicationRecord
   + has_many :records, foreign_key: 'author_id'
end
```
#### Note
The ``` foreign_key: 'author_id' ``` part is there because we had to explictly declare that the name of the foriegn key in the records
table is ```author_id``` and not  ```user_id``` , if we remove ``` foreign_key: 'author_id' ``` then active record thinks that the foriegn key column name is ```user_id``` and it results in conflict 

### Step 4
Modify the Record model code
```ruby
class Record < ApplicationRecord
   + belongs_to :author, class_name: 'User'
end
```
#### Note 
Again if we had followed conventions we would have just added ``` belongs_to :user ```












