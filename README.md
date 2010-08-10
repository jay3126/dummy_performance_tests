# Dummy performance tests

"Dummy performance tests" uses the routes generated by [dummy\_routes](http://github.com/goncalossilva/dummy_routes) to generate performance tests for your Rails 3 application.

## Description

"Dummy performance tests" generates performance tests for your Rails applications. It depends on the test routes generated by [dummy\_routes](http://github.com/goncalossilva/dummy_routes) 

## Installation

$ gem install dummy\_performance\_tests

## Usage 

Add the following to the Gemfile of your Rails 3 application:
    gem "dummy_performance_tests"
    
Now you have access to the generator:
    rails generate dummy:performance_tests
    
You need to tell it which directory was used when generating dummy routes (default: test/dummy):
    rails generate dummy:performance_tests --output-folder test/awesome_dummy

The files will be placed under _output-folder_/performance.
    
Feel free to mix all of these options.

The performance tests are stored in _test/dummy/performance_ (by default) while a rake file is placed in _lib/tasks/dummy\_performance.rake_. It allows you to run the previously generated tests:
    rake dummy:performance:test:all
    
The dummy data is copied from the development database into the database you specify (test, by default). The following would copy your development database to the "dummy" database for each test:
    RAILS_ENV="dummy" rake dummy:performance:test:all

Don't forget to import the data generated by dummy\_data into your development database before running the tests, otherwise they _will_ fail.

Results are stored in _test/dummy/results_ (by default). Two distinct printers are used:
  - GraphYamlPrinter for automated processing
  - CallStackPrinter for human processing

For these printers to be used correctly, put this in your Gemfile (the official mirror of ruby-prof is currently lacking the graph yaml printer):
    gem "ruby-prof", :git => "http://github.com/wycats/ruby-prof"

Copyright (c) 2010 Gonçalo Silva
