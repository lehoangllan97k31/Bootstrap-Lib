# Blog
Control Blog like the b0ss
=========================

## Installation new project
```sh
rails new blog
```

```sh
bundle install
```

```sh
rals server
```

```sh
localhost:3000
```

## Create Controller
```sh
rails generate controller "Pages" (name)
```


Create Page Welcome 
-> Create Action in pages_controller.rb
```ruby
	def welcome

	end
```

In pages (app/view) create new file Welcome.html.erb
In file Routes.rb (config),create route to Welcome Page
```sh
 get '/welcome' => 'pages/welcome'
```

How to use welcome is default page
In Routes.rb ,insert this top of page and delete "get '/welcome' ...."
 
```ruby
root to::'pages#welcome' 
```


## Build The Blog
CRUD (Create, Read, Update, Delete) -> Post

Create field for Post ( Tittle(string) and Content(test)) with
```ruby
rails generate scaffold Post tittle:string content:text
```

Megration Pending Error
Run in cmd
```sh
rails db::migrate RAILS_ENV=development
```

## Bootstrap 

Input Bootstrap to website
In view/layouts (main layouts of project) input this end of <head></head> the css's inputs and js's inputs
```ruby
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
```
```ruby
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>
```

Control Bootstrap

Layouts for Project
in <body></body>
create <div></div> tag look like this
```ruby
<div class="container">
    <%= yield %>
    </div>
```

Tables ( in views/post/index)
Forms ( in views/post/new) change field to name of forms in bootstrap and add id to field look like this
```ruby
<div class="form-group">
    <%= form.label :tittle %>
    <%= form.text_field :tittle, id: :post_tittle ,class:"form-control" %>
  </div>

  <div class="form-group">
    <%= form.label :content %>
    <%= form.text_area :content, id: :post_content,class:"form-control" %>
  </div>
```

	Create Home Page
Create Controller Home in cmd
```ruby
rails generate controller Home
```

In controller Home, inputs index 
```ruby
	def index

	end
```

In Routes.rb ,create root link look like
```ruby
	root to:"home#index"
```
Create new file "index.html.erb" with any inputs 

	Navbar
	Jumpbotron
	Grid ( truncate)
In homepages,want Post insert you must create the global var
```ruby
	posts = Post.new
```
And index.html.erb ,create Grid look like this
```ruby
<div class="row">
  <% @posts.each do |post| %>
  <div class="col-sm">
  	<h5><%= post.tittle%></h5>
    <p><%= truncate(post.content, length: 250) %></p>
    <%= link_to 'Read more', post_path(post) %>
  </div>
  <%end%>
</div>
```
Convert Navbar to "_navbar.html.erb" to layouts folder
in application.html.erb you must render navbar with this code in <body></body>
```ruby
<%= render 'layouts/navbar' %>
```
Using render to add a backsle file.


