## Windows Installation

If your a windows user using emoncms can you help complete this guide?

#### 1) Install WAMP

[http://www.wampserver.com/en/](http://www.wampserver.com/en/)

![WAMP](files/wampserver.png)

<br>

#### 2) Configure your server to accept mod rewrite

Emoncms makes use of htaccess mod_rewrite to create clean URL's while using the front controller and MVC architecture.

On Wampserver, enabling mod-rewrite is simply a case of left-click on your Wamp icon and hover on Apache, then hover over Apache Modules, then click PHP, then click on rewrite-module (you'll need to scroll down the list - it it's ticked, it's enabled). Do a restart all services on Wampserver.

#### 3) Enable gettext

The  "gettext" extension for Apache needs to be installed. Left-click on your Wamp icon and hover on PHP, then click on php.ini.  This will open the file in Notepad and you'll see the line about half-way way down (find "gettext"):
;extension=php_gettext.dll

it's commented out - remove the semi-colon and save the file. Do a restart all services on Wampserver.

#### 4) Create a MYSQL database

The easiest way to do this via a GUI is through a program called phpmyadmin. If you have a shared server you may need to do this through another mysql database setup program before you can access the database through phpmyadmin.

When, in phpmyadmin, the database has been created, a new user must also be created on host "localhost" (not "%") and have a password set.  When the user has been created, he needs to have "all" privileges over the new database that has just been created (scroll down for Database-specific privileges). Those 4 items - the new user name, password, "localhost" and database name are the values that go into the settings.php file. Note: this user isn't necessarily the same as one of the users who are allowed to register in emoncms once it's running.

#### 5) Download emoncms

    https://github.com/emoncms/emoncms

#### 6) Place emoncms in your WAMP public html directory

#### 7) Set emoncms settings.php

Copy default.settings.php and rename to settings.php. Enter your database username, password, server and database name.

#### 8) Thats it! Open emoncms in your browser

<div class='alert alert-info'>

<h3>Note: Browser Compatibility</h3>

<p><b>Chrome Ubuntu 23.0.1271.97</b> - developed with, works great.</p>

<p><b>Chrome Windows 25.0.1364.172</b> - quick check revealed no browser specific bugs.</p>

<p><b>Firefox Ubuntu 15.0.1</b> - no critical browser specific bugs, but movement in the dashboard editor is much less smooth than chrome.</p>

<p><b>Internet explorer 9</b> - works well with compatibility mode turned off. F12 Development tools -> browser mode: IE9. Some widgets such as the hot water cylinder do load later than the dial.</p>

<p><b>IE 8, 7</b> - not recommended, widgets and dashboard editor <b>do not work</b> due to no html5 canvas fix implemented but visualisations do work as these have a fix applied.</p>

</div>



