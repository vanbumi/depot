# Depot Application

## Steps

New application

    rails new depot -d postgresql

    cd depot

    rails s

Error

    FATAL: database "depot_development" does not exist

Setup database postgresql

    localhost:...
    username:...
    password:...

    rake db:create
    rake db:migrate

    rails s

Yay! You’re on Rails!

Create config/database-sample.yml

Git ignore

    /config/database.yml

    git init
    git add .
    git commit -m "Inital Depot Commit"

Create new repository on github.commit

    git remote add github git@github.com:vanbumi/depot.git
    git push github master

Create scaffold

    rails generate scaffold Product \
    title:string description:text image_url:string price:decimal    

> Note that command is too wide to fit comfortably on the page. To enter a
command on multiple lines, simply put a backslash as the last character on
all but the last line, and you’ll be prompted for more input.

refine the definition of the price to have eight digits of signifi-
cance and two digits after the decimal point.

    class CreateProducts < ActiveRecord::Migration[5.0]
      def change
        create_table :products do |t|
          t.string :title
          t.text :description
          t.string :image_url
          t.decimal :price, precision:8, scale:2

          t.timestamps
        end
      end
    end  

    rake db:migrate

    rails s

Try input some text on form products      

    rake:text

* the output should be two lines that each say 0 failures, 0 errors.
* This
is for the model and controller tests that Rails generates along with the scaffolding.

To import seed data, we simply modify the file in the db directory named seeds.rb.

    Product.delete_all
    Product.create!(title: 'CoffeeScript',
      description:
        %{<p>
            CoffeeScript is JavaScript done right. It provides all of JavaScript's
    	functionality wrapped in a cleaner, more succinct syntax. In the first
    	book on this exciting new language, CoffeeScript guru Trevor Burnham
    	shows you how to hold onto all the power and flexibility of JavaScript
    	while writing clearer, cleaner, and safer code.
          </p>},
      image_url:   'cs.jpg',    
      price: 36.00)
    # . . .
    Product.create!(title: 'Programming Ruby 1.9 & 2.0',
      description:
        %{<p>
            Ruby is the fastest growing and most exciting dynamic language
            out there. If you need to get working programs delivered fast,
            you should add Ruby to your toolbox.
          </p>},
      image_url: 'ruby.jpg',
      price: 49.95)
    # . . .

    Product.create!(title: 'Rails Test Prescriptions',
      description:
        %{<p>
            <em>Rails Test Prescriptions</em> is a comprehensive guide to testing
            Rails applications, covering Test-Driven Development from both a
            theoretical perspective (why to test) and from a practical perspective
            (how to test effectively). It covers the core Rails testing tools and
            procedures for Rails 2 and Rails 3, and introduces popular add-ons,
            including Cucumber, Shoulda, Machinist, Mocha, and Rcov.
          </p>},
      image_url: 'rtp.jpg',
      price: 34.95)

      rake db:seed

Update the style file /app/assets/stylesheets/products.css.scss

    <body class='<%= controller.controller_name %>'>
