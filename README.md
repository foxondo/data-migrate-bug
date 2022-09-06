# data_migrate bug example app

This is a minimal rails app to showcase a load issue with the (otherwise excellent) `data_migrate` gem. 

Versions used:
- ruby 3.1.2
- bundler 2.3.10
- data_migrate 8.1.1
- rails 7.0.3.1

see `Gemfile` and `Gemfile.lock` for more details.

## Problem

After checking out the app and running `bundle install`, a subsequent run of `bundle exec rails assets:clobber` will fail, because
no `database.yml` can be found, which hints to a DB connection being forced to be established.

If you remove `data_migrate` from the Gemfile and `bundle install` again, `bundle exec rails assets:clobber` will run flawlessly. 
(It does not matter whether we're using `rails assets:clobber` or `rake assets:clobber`)

## Fix

There is a proposed fix branch commented out in the `Gemfile`, which seems to alleviate the problem.
