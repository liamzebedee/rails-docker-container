Rails Docker container
======================

Using Fig and Docker, this is a simple and easy setup for a container for a Rails 4.1 application that uses Postgres as a database. Based off the [Fig guide for Rails](http://www.fig.sh/rails.html).

## Install
Install [Docker](https://docs.docker.com/installation/) and then [Fig](http://www.fig.sh/install.html) if you haven't already. Then follow these instructions (run using sudo on Ubuntu):
 1. Clone this repo and cd to it: `$ git clone https://github.com/liamzebedee/rails-docker-container && cd rails-docker-container`
 2. Create a new Rails app using fig that uses Postgres: `$ fig run web rails new . --force --database=postgresql --skip-bundle`
 3. Uncomment the line in your new Gemfile which loads therubyracer, so we've got a Javascript runtime: `gem 'therubyracer', platforms: :ruby`
 4. Build the Fig container: `$ fig build`
 5. Replace Rails' database config with our own: `$ mv database-new.yml config/database.yml`
 6. Setup the database: Boot the app by running `$ fig up` and in a **separate** terminal run `$ fig run web rake db:create`
 7. Visit `localhost:3000` and boom!
