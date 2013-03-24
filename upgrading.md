## Upgrading emoncms

### Upgrading to development branch (22 March 2013)

#### 1) Download the dev branch and place in a folder called dev

    https://github.com/emoncms/emoncms/tree/dev

If you use git, use **git clone** when installing for the first time:

    $ git clone -b dev git@github.com:emoncms/emoncms.git dev

and then all you need to call is

    $ git pull origin dev 

and it will download the latest changes.

#### 2) Set emoncms settings

Create a new copy of default.settings.php and call it settings.php.

    $ cp default.settings.php settings.php

Enter your database settings in to settings.php including username, password, database name and server.

#### 3) Run database update 

Open emoncms in your browser and login with the admin user - this will be the first user you created. Then navigate to the Admin tab (top-right). Click 'Update & check' this will update your database. If you get an error when you first login ignore it and go directly to:

    http://localhost/emoncms/admin 

#### 4) Run migrate_inputs.php script

Start by opening migrate_inputs.php in a text editor and removing the die; line which forces the script to exit. Then in your browser go to:

    http://localhost/emoncms/migrate_inputs.php

The script will list all the changes required. If your happy with the result, first backup your input table and then run migrate_inputs.php with the line $execute = false; set to true to automatically implement all the changes.

Once complete, disable the script again from accidental running by placing die at the top of the script, check that the result is a blank page when you try to run it again.

#### 5) Rename dev folder

If your happy that all the above steps went ok and you get no errors as you navigate through the development branch of emoncms in your browser then rename your old emoncms folder to something like emoncmsold and rename the dev branch folder to emoncms. This will allow any monitoring equipment to seemlessly start posting to the development branch.

If any of the pages look mysteriously empty, try clearing your browsers cache.

---

### Upgrading from older emoncms versions

If you have an emoncms version that is pre November 2012 it is likely that you have the version here [https://github.com/openenergymonitor/emoncms3](https://github.com/openenergymonitor/emoncms3) the current version is now in a different location as the change involved a large refactoring of emoncms code and with the new modular approach it made sense to keep all the emoncms repositories in one place rather than mixing with hardware firmware and other things. For more info see the [http://openenergymonitor.blogspot.com/2012/10/emoncms-development-update-modules.html](blog post).

If your upgrading from a pre November 2012 (emoncms3) to the current version [https://github.com/emoncms/emoncms](https://github.com/emoncms/emoncms) rename your old emoncms folder to something like emoncms_tmp as a backup until your happy that the new installation is fully working.

#### 1) Download the current version:

    https://github.com/emoncms/emoncms

If you use git, use **git clone** when installing for the first time:

    $ git clone git@github.com:emoncms/emoncms.git

and then all you need to call is

    $ git pull origin master 

and it will download the latest changes.

#### 2) Set emoncms settings

If you already have a settings.php file rename it to backup.settings.php.

    $ mv  settings.php backup.settings.php

Create a new copy of default.settings.php and call it settings.php.

    $ cp default.settings.php settings.php

Enter your database settings in to settings.php including username, password, database name and server.

#### 3) Run database update 

Open emoncms in your browser and login with the admin user - this will be the first user you created. Then navigate to the Admin tab (top-right). Click 'Update & check' this will update your database.

![db upgrade check](files/dbupdatecheck.png)

If you get an error, it may disappear if you run it a second time and the upgrade will complete as normal, this is a known bug.

#### 4) Complete the steps below that apply to you:

#### 15th November 2012 - Removal of feed_relation table and new userid field in feeds table.

If your upgrading from a pre November 2012 (emoncms3) to the current version https://github.com/emoncms/emoncms the new feeds module implementation associates a user with their feeds in a different way. This information is now stored in the feeds table rather than a seperate feed_relation table.

A small script has been created to make this conversion easy. In your emoncms directory you will see a script called **migrate.php** 

- Open this script in a text editor and remove the line that says die; so that you can run the script.
- Run the script in your browser, this is usually pretty quick.
- Once complete you can either remove the script or stop it from running again by re-entering die; at the top.

#### 15th July 2012 - New dashboard implementation

With the new dashboard implementation and the new visual dashboard editor dashboards created in versions of emoncms before mid-july 2012 no longer work with the current version as the dashboard renderer has been reworked. It is best to rebuild any dashboards using the new visual dashboard editor or the new ckeditor rebuild, there is a guide on how to do this in the using emoncms documentation.

#### 13th April 2012 - Feed tables now use integer timestamp, conversion needed.

If your emoncms version is pre 13th of April 2012, you will need to convert your feed tables from datetime to integer timestamp time format. A conversion script has been created to make this process easy. For this script line 13 needs to be uncommented before running it. For more information see [http://openenergymonitor.blogspot.com/2012/04/speeding-up-emoncms-feed-data-requests.html](http://openenergymonitor.blogspot.com/2012/04/speeding-up-emoncms-feed-data-requests.html)
