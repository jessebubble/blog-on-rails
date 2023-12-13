# Blog on Rails 
This is the blog application from the
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

## Introducng gems 
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

## The Rails directory structure 
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