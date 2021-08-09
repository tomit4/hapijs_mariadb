![](./hapijs.jpg)

<header>
<h4 style=color:#206557ff>A Default HapiJS/MariDB Server/Database Connection<h4>
</header>
<body>

<p style=color:#206557ff>This is just to have on hand should I need to set up a basic To do CRUD application for HapiJS with a MariaDB Database</p>

<header>
<h4 style=color:#206557ff>Install NodeJS<h4>
</header>

<p style=color:#206557ff>You'll first need NodeJS and it's package manager, NPM:</p>

<p style=color:#206557ff>From your terminal, enter:</p>

`sudo pacman -S nodejs npm`

<h4 style=color:#206557ff>Install MariaDB:</h4>

<p style=color:#206557ff>You'll need to spin up a MariaDB database that will persist your To Do List, so first you'll need to install MariaDB.
Installing MariaDB has multiple steps and is not as simple as inputting a single command, the following link is provided for your reference in installing MariaDB:</p>

<a style=color:#00ae8cff href="https://wiki.archlinux.org/title/MariaDB">Install MariaDB on Arch Linux</a>

<h5 style=color:#206557ff>After Installation:</h5>

<p style=color:#206557ff>Once MariaDB has been installed, you'll need to create a user and a password, as well as grant that user privileges to read/write from/to the database.  A simple way of creating this is to login to MariaDB as root:</p>

`sudo mariadb`

<p style=color:#206557ff>And create a user and password:</p>

`CREATE USER 'myname' @ 'localhost' IDENTIFIED BY 'mypassword'`

<p style=color:#206557ff>And grant that user all privileges (note that granting all privileges could be insecure, consider deleting user once testing this app is done):</p>

`GRANT ALL PRIVILEGES on *.* TO myname@localhost IDENTIFIED BY 'mypassword';`
`FLUSH PRIVILEGES`

<p style=color:#206557ff>Then we'll need to create a database, and then quit out of mariadb:</p>

`CREATE DATABASE <databasename;`
`\q`

<p style=color:#206557ff>This next part is optional, but you may want to start up your database whenever you start your computer, on Linux, this is done easily by entering the following command into your terminal:</p>

`sudo systemctl enable mariadb.service`

<p style=color:#206557ff>Alternatively, you can simply start mariadb by entering the following into your terminal:</p>

`sudo systemctl start mariadb.service`

<p style=color:#206557ff>And that should do it, we're finally ready to install the Vue Do It App:</p>

<h4 style=color:#206557ff>Install Vue Do It:</h4>

<p style=color:#206557ff>Next we'll need to actually download the project. Navigate to a directory you're comfortable with cloning the repository to.</p>

<h5 style=color:#206557ff>Clone the Repository:</h5>

`git clone https://github.com/tomit4/hapijs_mariadb.git`

<h5 style=color:#206557ff>Install Dependencies:</h5>

<p style=color:#206557ff>Navigate to your hapijs_mariadb directory, and from your terminal, enter:</p>

`npm install`

<p style=color:#206557ff>This will automatically install all dependencies necessary to run and test the application.</p>

<h5 style=color:#206557ff>Import The Database(not yet implemented</h5>

<p style=color:#206557ff>You'll also need to import the database.  I've provided a vue_do_it.sql file that can be imported like this, just make sure you created the database using the instructions above.  From the hapijs_mariadb directory, simply type into the terminal:</p>

`change this later:`
`mariadb -u username -p vue_do_it < vue_do_it.sql`

<h5 style=color:#206557ff>Create a .env-local file:</h5>

<p style=color:#206557ff>For security purposes, creating a .env-local file will pass sensitive login information to the server, first create the file:</p>

`touch .env-local`

<p style=color:#206557ff>And enter the following, each input on its on new line (no punctuation at the end of each line, be sure to put in your own mariadb username and password):</p>

`PORT=3000`
`DB_HOST=localhost`
`DB_USER=myname`
`DB_PASS=mypassword`
`DB_NAME=vue_do_it`

<h5 style=color:#206557ff>Start the Server:</h5>

<p style=color:#206557ff>To start the Servers (both localhost:3000 and localhost:8080 will be needed), simply navigate to your vue_do_it directory, and from your terminal, enter:</p>

`npm run hapi`

<p style=color:#206557ff>Open up your favorite browser, and in the address bar type:</p>

`localhost:3000`

<font size="2">

_This is meant to be used solely as a default boilerplate for using HapiJS with the NPM MariaDB module_
