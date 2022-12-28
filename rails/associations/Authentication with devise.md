# Authentication with devise

## Here are the steps to be implemented in order to add authentication via devise gem
- Add the following gem to your gem file
``` gem 'devise' ```
-  run ``` $ budle install ```
- Next, you need to run the generator:
```
$ rails generate devise:install
```
- Add the following line to the ``` config/environments/development.rb ```
```
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```
- Add the following tags to the end of the body tag in ```/app/views/layouts/application.html.erb```
```
 <p class="notice"><%= notice %></p>
 <p class="alert"><%= alert %></p>
```
- Next you need to connect devise with one of your models by running the following command replacing ```MODEL``` by the actual
name of the model you use (in most cases it is User model)
```
$ rails generate devise MODEL
````
- Run ``` rails db:migrate ```
- Run ``` $ rails generate devise:views users ``` to generate views like login form, sign-up form, etc...
- Go inside ```/app/views/devise/registrations/new.html.erb``` and add the missing fields for creating new user to the form
, for example if your users table has name and bio column then you need to add corresponding fields as shown below
 ```html
 <div class="field">
    <%= f.label :name %><br />
    <%= f.text_field :name, autofocus: true, autocomplete: "email" %>
 </div>
 <div class="field">
    <%= f.label :bio %><br />
    <%= f.text_field :bio, autofocus: true, autocomplete: "email" %>
 </div>
```
- Finnaly add the following code to the ```/app/controllers/application_controller.rb```
```ruby
  protect_from_forgery with: :exception

  before_action :update_allowed_parameters, if: :devise_controller?

  before_action :authenticate_user!

  protected

  def update_allowed_parameters
    devise_parameter_sanitizer.permit(:sign_up) { |u| u.permit(:name, :email, :password) }
    devise_parameter_sanitizer.permit(:account_update) { |u| u.permit(:name, :email, :password, :current_password) }
  end

  def after_sign_out_path_for(_resource_or_scope)
    request.referrer
    '/users/sign_in'
  end
```
- In order to have a way to log out use the button below some where on the page
```
<%= button_to "logout", destroy_user_session_path, method: :delete,class:"btn btn-light" %>
```

### Useful links
- [Official guide from devise repositort](https://github.com/heartcombo/devise#getting-started)
