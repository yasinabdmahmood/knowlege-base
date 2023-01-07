# Routing in rails
Basic Syntax:
```ruby 
get '/photos', to: 'photos#index'
```
This will create a route that maps the root URL `/photos` to the `index` action in the `PhotosController`.

```ruby
get '/photos/:id', to: 'photos#show'
```
This will create a route that maps URLs like `/photos/1`, `/photos/2`, etc. to the `show` action in the `PhotosController`. The :id part is a placeholder for the actual ID of the photo. its value can be accessed in controller action by `params[:id]`


