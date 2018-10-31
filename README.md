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
root to:'pages#welcome' 
```





