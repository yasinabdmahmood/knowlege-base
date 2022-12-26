# Validations
validations come in form of ruby methods added to the model classes

## Cheatsheet
```ruby
class User < ApplicationRecord
  # name column must be present
  validates :name, presence: true
  
  #name column must be no longer than 50 character
  validates :name, length: { maximum: 50 }
  
  # User model must be associated with Record model
  validates_associated :records
  # Note : association validation above works for every kind of validation
  #and must be added to only one end of the association
  
  # amount column must be number
  validates :amount, numericality: true
  
  # games_played column must be integer
  validates :games_played, numericality: { only_integer: true }
  
   # games_played column must be grater than or equal to 5
  validates :games_played, numericality: { :greater_than_or_equal_to: 5 }
end
```
## Useful links

[official rails documantation about validation](https://guides.rubyonrails.org/active_record_validations.html#validations-overview)
