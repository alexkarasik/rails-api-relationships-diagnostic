# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
  Join tables link the relationships between different tables together.
  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
  I am a bit off with my synax and know I am missing a few things.
  Profiles and Movies are two seperate tables that are connected by the Favorites join table.
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
    has_many: given_name, surname, email through: :favorites
    has_many :favorites
  end
  ```

  ```rb
  class Movie < ActiveRecord::Base
    had_many: release_date, length through: :favorites
    has_many: favorites
  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
    belongs_to :movie
    belongs_to :profile
  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
A serializer gives us custom JSON by giving us each resource as a class that inherits from the serializer.
https://www.sitepoint.com/active-model-serializers-rails-and-json-oh-my/
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
  No time
  end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
  rails generate scaffold Favorites movies:string profiles:string
  ```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
  Dependent is concerned with associated objects when their owner is destroyed. Destroy is when the associated objects are themselves destroyed. If we had seperate tables of parent and child elements, it saves time and secures that there are no mistakes when we want both the parents and the children destroyed.

  http://stackoverflow.com/questions/20915443/dependent-destroy-how-does-this-work
  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md
  One to many is when a parent record in one table can reference several child records. The child record can not have more than one parent record, but the parent record can have multiple or even no child records.
  A mother can have many children, but those children only have one mother.
  For a many-to-many relationship, a child record can link to several parents records
  An author can write several books and a book can have several authors.
  ```
