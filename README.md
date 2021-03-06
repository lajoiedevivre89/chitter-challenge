# Chitter Challenge



### Chitter is a clone of the popular micro-blogging service Twitter.

* This version has a responsive top navigation menu.

* A user can **sign up** for a Chitter account, **log in** and **log out.**

* They can **post** messages and see them in **reverse chronological order** on their page, with the **time** that the message was created, alongside the message.

* 100% test coverage


### Database creation

The Chitter Challenge uses **PostgreSQL**, so if you don't have it installed on your computer, please do the following:

**Install postgres:**

```html
brew install postgresql
```

**Start postgres:**

```
brew services start postgresql
psql postgres
```


**Create database:**

```html
CREATE DATABASE chitter;
```


**Create a test database:**

```html
CREATE DATABASE chitter_test;
```


### Connect to the chitter database by typing:

```html
\c chitter
```

**Create the following tables and alterations, by typing the following SQL commands:
(the commands should be executed in order)**

```html
CREATE TABLE messages(id SERIAL PRIMARY KEY, name VARCHAR(40), peep_handle VARCHAR(20), message VARCHAR(400));
```

```html
ALTER TABLE messages ADD COLUMN posted_at TIMESTAMP DEFAULT NOW(); 
```

```html
CREATE TABLE users(id SERIAL PRIMARY KEY, email VARCHAR(40), password VARCHAR(100), peep_handle VARCHAR(40));
```

```html
ALTER TABLE messages ADD COLUMN user_id INTEGER REFERENCES users (id);
```

```html
ALTER TABLE messages DROP COLUMN name;
```

```html
ALTER TABLE messages DROP COLUMN peep_handle;
``` 


Check that the tables have been created by typing the following: 

```html
\dt
```

**Repeat for the test database - chitter_test**


### How to use:

**Clone this repository:**

```html
git clone https://github.com/emilyjspencer/chitter-challenge.git
```

**cd into the repo on your computer**

Run:
```html
bundle install
```

**Start the server:**

```html
rackup
```

**Go to localhost:9292**


### How to run the tests

* Type the following into the terminal: 
```html
rspec
```

## Built with

* Ruby
* Sinatra
* HTML/CSS
* SQL 

## Tested with

* RSpec
* Capybara 

### What it looks like:

![homepage](updated_home.png)
![homepage2](index2.png)
![signup](signup.png)
![login](login.png)
![welcomeuser](welcome_user.png)
![messages](messages.png)












=================

* Challenge time: rest of the day and weekend, until Monday 9am
* Feel free to use Google, your notes, books, etc. but work on your own
* If you refer to the solution of another coach or student, please put a link to that in your README
* If you have a partial solution, **still check in a partial solution**
* You must submit a pull request to this repo with your code by 9am Monday morning

Challenge:
-------

As usual please start by forking this repo.

We are going to write a small Twitter clone that will allow the users to post messages to a public stream.

Features:
-------

```
STRAIGHT UP

As a Maker
So that I can let people know what I am doing  
I want to post a message (peep) to chitter

As a maker
So that I can see what others are saying  
I want to see all peeps in reverse chronological order

As a Maker
So that I can better appreciate the context of a peep
I want to see the time at which it was made

As a Maker
So that I can post messages on Chitter as me
I want to sign up for Chitter

HARDER

As a Maker
So that only I can post messages on Chitter as me
I want to log in to Chitter

As a Maker
So that I can avoid others posting messages on Chitter as me
I want to log out of Chitter

ADVANCED

As a Maker
So that I can stay constantly tapped in to the shouty box of Chitter
I want to receive an email if I am tagged in a Peep
```

Technical Approach:
-----

This week you integrated a database into Bookmark Manager using the `PG` gem and `SQL` queries. You can continue to use this approach when building Chitter Challenge.

If you'd like more technical challenge this weekend, try using an [Object Relational Mapper](https://en.wikipedia.org/wiki/Object-relational_mapping) as the database interface.

Some useful resources:
**DataMapper**
- [DataMapper ORM](https://datamapper.org/)
- [Sinatra, PostgreSQL & DataMapper recipe](http://recipes.sinatrarb.com/p/databases/postgresql-datamapper)

**ActiveRecord**
- [ActiveRecord ORM](https://guides.rubyonrails.org/active_record_basics.html)
- [Sinatra, PostgreSQL & ActiveRecord recipe](http://recipes.sinatrarb.com/p/databases/postgresql-activerecord?#article)

Notes on functionality:
------

* You don't have to be logged in to see the peeps.
* Makers sign up to chitter with their email, password, name and a username (e.g. samm@makersacademy.com, password123, Sam Morgan, sjmog).
* The username and email are unique.
* Peeps (posts to chitter) have the name of the maker and their user handle.
* Your README should indicate the technologies used, and give instructions on how to install and run the tests.

Bonus:
-----

If you have time you can implement the following:

* In order to start a conversation as a maker I want to reply to a peep from another maker.

And/Or:

* Work on the CSS to make it look good.

Good luck and let the chitter begin!

Code Review
-----------

In code review we'll be hoping to see:

* All tests passing
* High [Test coverage](https://github.com/makersacademy/course/blob/master/pills/test_coverage.md) (>95% is good)
* The code is elegant: every class has a clear responsibility, methods are short etc.

Reviewers will potentially be using this [code review rubric](docs/review.md).  Referring to this rubric in advance may make the challenge somewhat easier.  You should be the judge of how much challenge you want this weekend.

Automated Tests:
-----

Opening a pull request against this repository will will trigger Travis CI to perform a build of your application and run your full suite of RSpec tests. If any of your tests rely on a connection with your database - and they should - this is likely to cause a problem. The build of your application created by has no connection to the local database you will have created on your machine, so when your tests try to interact with it they'll be unable to do so and will fail.

If you want a green tick against your pull request you'll need to configure Travis' build process by adding the necessary steps for creating your database to the `.travis.yml` file.

- [Travis Basics](https://docs.travis-ci.com/user/tutorial/)
- [Travis - Setting up Databases](https://docs.travis-ci.com/user/database-setup/)

Notes on test coverage
----------------------

Please ensure you have the following **AT THE TOP** of your spec_helper.rb in order to have test coverage stats generated
on your pull request:

```ruby
require 'simplecov'
require 'simplecov-console'

SimpleCov.formatter = SimpleCov::Formatter::MultiFormatter.new([
  SimpleCov::Formatter::Console,
  # Want a nice code coverage website? Uncomment this next line!
  # SimpleCov::Formatter::HTMLFormatter
])
SimpleCov.start
```

You can see your test coverage when you run your tests. If you want this in a graphical form, uncomment the `HTMLFormatter` line and see what happens!



