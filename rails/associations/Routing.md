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
<br>

```ruby
resources :photos
```
This will create a set of routes for a "resource" (a set of similar objects, such as photos). It will create routes for the `index`, `show`, `new`, `create`, `edit`, `update`, and `destroy` actions, using RESTful conventions.

## Named Routes:
```ruby
get '/photos/:id', to: 'photos#show', as: 'photo'
```
This will create a route with the name `photo`. You can then use this name in your views to generate URLs:
```ruby
<%= link_to 'Show photo', photo_path(@photo) %>
```
This will generate a link like `/photos/1` (assuming @photo has an ID of `1`).
<br>
```ruby
<%= link_to 'Edit photo', edit_photo_path(@photo) %>
```
<br>
```ruby
<%= form_for @photo, url: photo_path(@photo), method: :delete do |f| %>
  <%= f.submit 'Delete' %>
<% end %>
```
This will create a form that submits a `DELETE` request to the URL `/photos/1` (assuming @photo has an ID of `1`).

<br>
## Redirects:
```ruby
redirect_to '/photos'
```
This will redirect the user to the `/photos` URL.
<br>
```ruby
redirect_to @photo
```
This will redirect the user to the URL of the `@photo` object (e.g. `/photos/1` if @photo has an ID of `1`).





