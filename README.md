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
