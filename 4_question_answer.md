Hello brother .....

I would like to help you with the question that you are asking yousel about plurality and singularity in rails.

It is true that it often confuse to people who are new to Rails. 

so here I am going to help you with naming conversion of rails

# Rails naming conventions

## Database

Database tables are always in lower cases. Table names are plural.

Column names in the database use lower cases too, but are generally singular. and when you right names make sure to obey sql rules of database


| blogs       | 
| ------------- |
| id      | 
| blog_name      | 
| blog_title | 

## Model

Model class names are written in starting with upper case(Blog) . These are singular, and will map automatically to the plural database table name.

Model attributes and methods use lower case and match the column names in the database.

Model files go in app/models/#{singular_model_name}.rb.

Example:

>```ruby
># app/models/my_blog.rb
>class MyBlog < ActiveRecord::Base
>  # This class will have these attributes: id, sighted_at, location
>end
>```

>```ruby
># app/models/blog.rb
>class Blog < ActiveRecord::Base
>  # Methods follow the same conventions as attributes
>  def mark
>    id > 2
>  end
>end
>```

## Relations in models

Relations use lower cases and follow the type of relation, so `has_one` and `belongs_to` are singular while `has_many` is plural.

Rails expects foreign keys in the database to have an _id suffix, and will map relations to those keys automatically if the names line up.

Example:

>```ruby
># app/models/my_blog.rb
>class MyBlog < ActiveRecord::Base
>  # This knows to use the blog_id field in the database
>  belongs_to :blog
>end
>```

>```ruby
># app/models/blog.rb
>class Blog < ActiveRecord::Base
>  # This knows to look at the MyBlog class and find the foreign key in that table
>  has_many :my_blogs
>end
>```

## Controller

Controller class names use `CamelCase` and have `Controller` as a suffix. The `Controller` suffix is always singular. The name of the resource is usually plural.

Controller actions use `snake_case` and usually match the standard route names Rails defines (`index`, `show`, `new`, `create`, `edit`, `update`, `delete`).

Controller files go in `app/controllers/#{resource_name}_controller.rb.`

Example:

>```ruby
># app/controllers/my_blogs_controller.rb
>MyBlogsController < ApplicationController
>  def index
>    # ...
>  end
>  def show
>    # ...
>  end
>  # etc
>end
>```

>```ruby
># app/controllers/blogs_controller.rb
>BlogsController < ApplicationController
>  def show
>    # ...
>  end
>  # etc
>end
>```

## Routes

Route names are `snake_case`, and usually match the controller. Most of the time routes are plural and use the plural `resources`.

http://edgeguides.rubyonrails.org/routing.html#singular-resources are a special case. These use the singular resource and a singular resource name. However, they still map to a plural controller by default!

Example:

>```ruby
>resources :my_blogs
># Users can only see their own profiles, so we'll use `/profile` instead
># of putting an id in the URL.
>resource :blog
>```

## Views
View file names, by default, match the controller and action that they are tied to.

Views go in `app/views/#{resource_name}/#{action_name}.html.erb.`

Examples:

* app/views/bigfoot_sightings/index.html.erb
* app/views/bigfoot_sightings/show.html.erb
* app/views/profile/show.html.erb

# More resources

* http://edgeguides.rubyonrails.org/active_record_basics.html#naming-conventions

* https://teddicodes.files.wordpress.com/2015/02/railsnamingconventions.pdf

