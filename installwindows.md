## Windows Installation

If your a windows user using emoncms can you help complete this guide?

#### 1) Install WAMP

[http://www.wampserver.com/en/](http://www.wampserver.com/en/)

![WAMP](files/wampserver.png)

<br>

#### 2) Configure your server to accept mod rewrite

Emoncms makes use of htaccess mod_rewrite to create clean URL's while using the front controller and MVC architecture.

This may help: [http://blog.cmstutorials.org/tutorials/tips-tricks/how-to-make-mod_rewrite-work-on-wamp](http://blog.cmstutorials.org/tutorials/tips-tricks/how-to-make-mod_rewrite-work-on-wamp)

#### 3) Create a MYSQL database

The easiest way to do this via a GUI is through a program called phpmyadmin. If you have a shared server you may need to do this through another mysql database setup program before you can access the database through phpmyadmin.

#### 4) Download emoncms

    https://github.com/emoncms/emoncms

#### 5) Place emoncms in your WAMP public html directory

#### 6) Set emoncms settings.php

Copy default.settings.php and rename to settings.php. Enter your database username, password, server and database name.

#### 7) Thats it! Open emoncms in your browser
 
**(Optional) Enable Multi lingual support using gettext**

Not sure how to do this in windows but here is how its done in ubuntu linux which may give some clues, step 4 onwards: 

[http:/openenergymonitor.org/emon/emoncms/using-gettext-on-ubuntu](http://openenergymonitor.org/emon/emoncms/using-gettext-on-ubuntu)

<br>
