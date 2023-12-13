# Blog on Rails 
This is the blog application from
[*Getting Started with Rails*](http://guides.rubyonrails.org/getting_started.html)

## Introducing Ruby
**Ruby** is a dynamic, open source programming language developed by Yukihiro "Matz" Matsumoto in the mid-1990s. Ruby's combination of expressiveness, simplicity, and flexibility has made it a popular choice for both beginners and experienced developers. It's used for a wide range of applications, from web development with Ruby on Rails to scripting and automation. The language continues to evolve with new features and improvements while maintaining its core principles.

## Introducing rbenv
**rbenv** is a versatile Ruby version manager that provides a lightweight and flexible solution for managing Ruby environments. It's particularly beneficial for developers working on multiple projects with varying Ruby version requirements. 
<br />
<br />
Without impacting the version of Ruby that ships with macOS, rbenv lets you seamlessly switch between multiple Ruby versions and allows you to set Ruby versions on a per-project basis.

```bash
# Install Ruby version 3.2.2 with rbenv
rbenv install 3.2.2
```

## Introducing gems 
**gems** play a crucial role in the Ruby ecosystem by promoting code reuse, collaboration, and efficient management of project dependencies. They simplify the process of sharing and distributing Ruby code, contributing to the vibrancy and productivity of the Ruby programming community.

```bash
# Install the bundler gem
gem install bundler
``` 

## Introducing Rails
Ruby on Rails is a web application framework that is built on the Ruby programming language. It simplifies web development by providing conventions, abstractions, and tools that enable developers to build robust and maintainable applications with less boilerplate code. The combination of Ruby's expressiveness and Rails' conventions contributes to the popularity and effectiveness of the framework in creating modern web applications.

```bash
# Install Rails with gem
gem install rails
```

## The Rails directory
The `blog-on-rails` directory will have a number of generated files and folders that make
up the structure of a Rails application. Most of the work in this tutorial will
happen in the `app` folder, but here's a basic rundown on the function of each
of the files and folders that Rails creates by default:

| File/Folder | Purpose |
| ----------- | ------- |
|app/|Contains the controllers, models, views, helpers, mailers, channels, jobs, and assets for your application. You'll focus on this folder for the remainder of this guide.|
|bin/|Contains the `rails` script that starts your app and can contain other scripts you use to set up, update, deploy, or run your application.|
|config/|Contains configuration for your application's routes, database, and more. This is covered in more detail in [Configuring Rails Applications](configuring.html).|
|config.ru|Rack configuration for Rack-based servers used to start the application. For more information about Rack, see the [Rack website](https://rack.github.io/).|
|db/|Contains your current database schema, as well as the database migrations.|
|Dockerfile|Configuration file for Docker.|
|Gemfile<br>Gemfile.lock|These files allow you to specify what gem dependencies are needed for your Rails application. These files are used by the Bundler gem. For more information about Bundler, see the [Bundler website](https://bundler.io).|
|lib/|Extended modules for your application.|
|log/|Application log files.|
|public/|Contains static files and compiled assets. When your app is running, this directory will be exposed as-is.|
|Rakefile|This file locates and loads tasks that can be run from the command line. The task definitions are defined throughout the components of Rails. Rather than changing `Rakefile`, you should add your own tasks by adding files to the `lib/tasks` directory of your application.|
|README.md|This is a brief instruction manual for your application. You should edit this file to tell others what your application does, how to set it up, and so on.|
|storage/|Active Storage files for Disk Service. This is covered in [Active Storage Overview](active_storage_overview.html).|
|test/|Unit tests, fixtures, and other test apparatus. These are covered in [Testing Rails Applications](testing.html).|
|tmp/|Temporary files (like cache and pid files).|
|vendor/|A place for all third-party code. In a typical Rails application this includes vendored gems.|
|.dockerignore|This file tells Docker which files it should not copy into the container.|
|.gitattributes|This file defines metadata for specific paths in a git repository. This metadata can be used by git and other tools to enhance their behavior. See the [gitattributes documentation](https://git-scm.com/docs/gitattributes) for more information.|
|.gitignore|This file tells git which files (or patterns) it should ignore. See [GitHub - Ignoring files](https://help.github.com/articles/ignoring-files) for more information about ignoring files.|
|.ruby-version|This file contains the default Ruby version.|

## Starting up the Web Server
Blog-on-Rails is a functional Rails application. To see it, you need to start a web server on your development machine. You can do this by running the following in the `blog-on-rails` directory:

```bash
# Start the web server
bin/rails server
```

## Introducing puma
**Puma** is a versatile web server designed to handle concurrent requests efficiently, making it a suitable choice for serving Ruby on Rails applications. Its multi-process and multi-threaded architecture, along with features like load balancing and graceful restarts, make it well-suited for deploying web applications in production environments. By default, Puma is distributed by Rails with every new application generated by the `rails new` command.

## MVC
Ruby on Rails follows the **Model-View-Controller** architectural pattern to structure web applications. This separation of concerns enhances maintainability, scalability, and code organization. Each component plays a specific role in handling user requests, managing data, and presenting the user interface. The Rails framework provides a set of conventions and tools that make it easy for developers to follow MVC principles while building robust and scalable web applications

### Models on Rails
- The **Model** is typically implemented as Ruby classes that interact with the database. Each model class corresponds to a database table, and instances of the class represent records in that table.
- Rails uses an **Object-Relational Mapping (ORM)** system called **Active Record** to facilitate communication between the application and the database. Active Record simplifies database operations and allows developers to work with databases using Ruby objects.

### Views on Rails
- The **View** is implemented using templates. **Templates** are typically written in **Embedded Ruby (ERB)** or another templating language. ERB allows Ruby code to be embedded within HTML, facilitating dynamic content generation.
- Views in Rails are associated with Controller actions, and they render the HTML that is sent to the user's browser. Views can access data provided by the Controller and present it to the user.

### Controllers on Rails
- The **Controller** is implemented as Ruby classes. Each Controller class is associated with a set of actions (methods) that correspond to user requests. For example, a UserController might have actions like `index`, `show`, `create`, etc.
- The Controller communicates with the Model to retrieve or modify data and then selects the appropriate View to render. Controllers handle routing, request processing, and coordinating the flow of data between the Model and View.

## Introducing Active Record
**Active Record** is a core component of Ruby on Rails, serving as the ORM that **connects Rails models to database tables**. It simplifies database interactions, provides a rich set of functionalities for working with data, and aligns with Rails conventions to enhance developer productivity and code maintainability

> **Object-Relational Mapping (ORM)** <br/>
>ORM is a programming technique that maps objects in a programming language (like Ruby) to tables in a relational database. It simplifies database interactions by allowing developers to interact with the database using high-level programming constructs rather than writing raw SQL queries

```bash
# Define a model in Rails
# To define a model in Rails, you create a Ruby class that inherits from ActiveRecord::Base. This base class provides a set of methods and functionalities that allow the model to interact with the database

class User < ApplicationRecord::Base
end
```

```bash
# DB table mapping
# By convention, Active Record infers the database table name based on the class name and pluralization. 

#For example, the User class maps to the users table
class User < ApplicationRecord::Base
    self.table_name = "my_users"
    self.primary_key = "user_id"
end
```

```bash
# CRUD operations
# Active Record provides methods for performing CRUD (Create, Read, Update, Delete) operations on database records

# Create a new user
user = User.new(name: "Elton John", email: "elton@rocketman.com")
user.save

# Find a user by ID
found_user = User.find(1)

# Update a user's attributes
found_user.update(name: "Elton Hercules John")

# Delete a user
found_user.destroy
```

```bash
# Associations
# Active Record supports defining associations between models, such as `has_many`, `belongs_to`, and `has_and_belongs_to_many`. These associations simplify the representation of relationships between tables.

class User < ApplicationRecord::Base
    has_many :posts
end

class Post < ApplicationRecord::Base
    belongs_to :user
end
```

```bash
# Validations
# Active Record includes validation mechanisms that allow developers to specify rules for data integrity. Common validations include presence, uniqueness, format, and custom validations

class User < ApplicationRecord::Base
    validates :email, presence: true
end
```

```bash
# Callbacks
# Active Record provides callbacks, such as `before_save`, `after_create`, and `before_validation`, allowing developers to execute code at specific points in the lifecycle of a model

class User < ApplicationRecord::Base
    before_save :normalize_name

    private

    def normalize_name
        self.name = name.downcase.titleize
    end
end
```

```bash
# Querying
# Active Record includes a powerful query interface that allows developers to construct complex database queries using a Ruby-like syntax

User.where(name: "Elton John")
```

```bash
# Connecting to a database
# Active Record manages database connections, and Rails provides configuration settings (in `config/database.yml`) for specifying database connection details

development:
    adapter: sqlite3
    database: db/development.sqlite3
```

```bash
# Migrations
# Active Record includes a migration system that allows developers to version-control and automate changes to the database schema over time

class CreateUsers < ActiveRecord::Migration[6.1]
    def change
        create_table :users do |t|
            t.string :name
            t.string :email
            t.timestamps
        end
    end
end
```

## Introducing irb (Interactive Ruby)
**IRB** is an interactive Ruby shell that provides a convenient way for developers to experiment with Ruby code. When used within the context of a Rails application, such as through the **rails console command**, IRB becomes a powerful tool for interacting with and testing various aspects of the Rails environment, including models, controllers, and the database. It's a valuable tool for debugging, exploration, and quick testing within the Rails ecosystem.

Let's launch the **Rails console** with this command:

```bash
$ bin/rails console
```

You should see an `irb` prompt like:

```irb
Loading development environment (Rails 7.2.0)
irb(main):001:0>
```

At this prompt, we can initialize a new `Article` object:

```irb
irb> article = Article.new(title: "Hello Rails", body: "I am on Rails!")
```

It's important to note that we have only *initialized* this object. This object
is not saved to the database at all. It's only available in the console at the
moment. To save the object to the database, we must call [`save`](
https://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-save):

```irb
irb> article.save
(0.1ms)  begin transaction
Article Create (0.4ms)  INSERT INTO "articles" ("title", "body", "created_at", "updated_at") VALUES (?, ?, ?, ?)  [["title", "Hello Rails"], ["body", "I am on Rails!"], ["created_at", "2020-01-18 23:47:30.734416"], ["updated_at", "2020-01-18 23:47:30.734416"]]
(0.9ms)  commit transaction
=> true
```

The above output shows an `INSERT INTO "articles" ...` database query. This
indicates that the article has been inserted into our table. And if we take a
look at the `article` object again, we see something interesting has happened:

```irb
irb> article
=> #<Article id: 1, title: "Hello Rails", body: "I am on Rails!", created_at: "2020-01-18 23:47:30", updated_at: "2020-01-18 23:47:30">
```

The `id`, `created_at`, and `updated_at` attributes of the object are now set.
Rails did this for us when we saved the object.

When we want to fetch this article from the database, we can call [`find`](
https://api.rubyonrails.org/classes/ActiveRecord/FinderMethods.html#method-i-find)
on the model and pass the `id` as an argument:

```irb
irb> Article.find(1)
=> #<Article id: 1, title: "Hello Rails", body: "I am on Rails!", created_at: "2020-01-18 23:47:30", updated_at: "2020-01-18 23:47:30">
```

And when we want to fetch all articles from the database, we can call [`all`](
https://api.rubyonrails.org/classes/ActiveRecord/Scoping/Named/ClassMethods.html#method-i-all)
on the model:

```irb
irb> Article.all
=> #<ActiveRecord::Relation [#<Article id: 1, title: "Hello Rails", body: "I am on Rails!", created_at: "2020-01-18 23:47:30", updated_at: "2020-01-18 23:47:30">]>
```

This method returns an [`ActiveRecord::Relation`](
https://api.rubyonrails.org/classes/ActiveRecord/Relation.html) object, which
you can think of as a super-powered array.

>To learn more about models, see [Active Record Basics](active_record_basics.html) and [Active Record Query Interface](active_record_querying.html).

## Introducing ERB (Embedded Ruby)
Ruby on Rails primarily uses **ERB (Embedded RuBy)** as its default templating system for generating dynamic content in **views**. ERB allows developers to embed Ruby code within HTML or other text documents, making it easy to create dynamic web pages.

> **Templating Languages** <br/>
> Templating languages enable the seamless integration of dynamic content, facilitate the separation of concerns, and provide tools for handling user input and generating HTML with embedded code. They contribute to the overall efficiency and structure of web development projects

```erb
<!-- Basic ERB syntax -->
<!-- ERB tags are delimited by <% %> and <%= %> -->
<!-- The <% %> tag is used for embedding Ruby code that doesn't need to be displayed -->
<!-- The <%= %> tag is used for embedding Ruby code that needs to be displayed -->

<!-- app/views/users/index.html.erb -->
<h1> Hello, <%= @user.name %>! </h1>
```

```erb
<!-- ERB control flow -->
<!-- ERB tags can be used to implement control flow constructs like if/else, while, and for loops -->

<!-- app/views/users/index.html.erb -->
<% if @user.name == "Elton John" %>
    <h1> Hello, <%= @user.name %>! </h1>
<% else %>
    <h1> Hello, stranger! </h1>
<% end %>
```
    
```erb
<!-- ERB partials -->
<!-- ERB partials are reusable templates that can be rendered within other templates -->
<!-- Partials are typically used to render common elements like headers, footers, and navigation bars -->

<!-- app/views/users/index.html.erb -->
<%= render partial: "header" %>
<h1> Hello, <%= @user.name %>! </h1>
<%= render partial: "footer" %>
```
