## Upgrading emoncms


### Upgrading from version 4.0 to 5.0

**Note:** Version 4.0 was commonly refered to as modular emoncms. 

#### 1) Download
Download the latest version either by clicking on the zip icon in github or if you previously used git clone you can download the latest changes with:

    $ git pull origin master
    
#### 2) Settings.php
Make a copy of your current *settings.php* file and create a new *settings.php* anew from *default.settings.php* Enter your emoncms database settings.

Add the following line to the bottom of *settings.php* to enable a special database update only session, be sure to remove this line from settings.php once complete:
 
    $updatelogin = true;
    
#### 3) Run the database updater
In your internet browser open the admin/view page and click on the database update and check button to launch the database update script.

    http://localhost/emoncms/admin/view
    
You should now see a list of changes to be performed on your existing emoncms database.
You may at this point want to backup your input and users table before applying the changes.

#### 4) If you're running emoncms on a Raspberry Pi with an RFM12Pi and RaspberryPi emoncms module
You will need to remove the cron job entry for the PHP gateway script. Run 
    
    $ sudo nano/etc/crontab 
    
and remove the entry with emoncms php. Now restart the Pi. The new Deamon script should be runnning see RaspberryPi emoncms module Github Readme for info on how to check

That should be it.

#### Troubleshooting

You may need to clear your browser cache if an interface appears buggy.


### Upgrading from older versions, version 2 and 3

Upgrade scripts for older versions will be reintroduced very soon, which will make this much easier.

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
