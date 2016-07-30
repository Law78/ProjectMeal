# ProjectMeal - on Linux

Ho messo le seguenti versioni nel gemfile:
ruby '2.3.1'

gem 'rails', '4.2.6'

gem 'sprockets', '3.7.0'
gem 'sass-rails', '5.0.6'

Lancio: bundle update inserendo la password di root
Ma ho avuto problemi nell'installazione di bcrypt.
Gli errori saranno del tipo:

extconf.rb mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h
Error message: Make sure that `gem install pg -v '0.18.1'` succeeds before bundling
An error occurred while installing pg

Ora sto installando:

sudo apt-get install ruby-dev

e riprovando il comando:
sudo gem install bcrypt -v '3.1.11'

si è installato. Lancio di nuovo il comando: bundle update

Adesso ho problemi con mysql2, provato anche nella versione 0.4.4.
Sto provando installando mysql:

sudo apt-get update
sudo apt-get install mysql-server-5.7 libmysqlclient-dev

Provo a rifare bundle update
e' andato, ma ora il problema è sulla gemma pg, quella di Postgre.
A questo punto lancio

sudo apt-get install postgresql

e rilancio bundle update

Niente. Lancio il comando:
sudo apt-get install libpq-dev

di nuovo: bundle update
e ho risolto tutto.