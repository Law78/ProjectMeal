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

Da terminale ho scritto:
sudo -u postgres psql postgres

Dalla shell di postgres ho inserito il comando:
\password postgres

e inserito la password per l'utente postgres.
Poi ho fatto \quit per uscire.

Ho installato pgAdmin con il comando da terminale:
sudo apt install pgAdmin3

Avvio pgAdmin3, ho trovato l'icona sotto Programmazione e creo un utente lorenzo
(NON L'ho fatto!!!)(Ora vado ad editare il file di configurazione:
cd /etc/postgresql/9.5/main
sudo vi pg_ident.conf)
Ora da terminale posso scrivere:
psql lorenzo -h 127.0.0.1 -d mydb

dove lorenzo è lo user che ho creato da pgAdmin3 e mydb il db creato sempre da
pgAdmin3. Attenzione che il nome utente è case sensitive.

Mentre per MySQL sono andato a scaricare il MySQL Workbench direttamente dal
sito MySQL, in cui trovo il .deb
Lancio l'applicazione e creo l'utente lorenzo :)

#Lezione 5
Ho creato il db manualmente da mysql workbench. Ma potevo crearlo tramite comandi rake db:create.

Lanciando il comando rails generate controllers Catalogues io non ho trovato nessuna modifica al file routes, per cui ho rilanciato il comando aggiungendo una action index. Questa mi crea il layout sotto views-catalogues chiamato index.html.erb e nel controller il metodo:
def index
end
Oltre al route in routes.
Ho voluto però scrivere in routes (togliendo ciò che mi ha generato):
resources :catalogues

Poi ho creato il metodo:
def show
end

ed il file, sotto views-catalogues, show.html.erb scrivendo un semplice h1.

Perfetto, funge.
