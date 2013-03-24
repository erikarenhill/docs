## Troubleshooting

#### If you get a 404 not found when you click on home or register

This is probably because you need to enable mod rewrite on your server. See step 4 of the Linux guide and step 2 of the windows guide.

#### If you get an mysql cannot write into database error

Check that the database settings in settings.php are correct and that the database user has full rights to the database.

#### If you try to upgrade emonCMS with an old database and you get this error: 

    Fatal error: Call to a member function fetch_array() on a non-object in ../Includes/db.php on line 50

It is because the database schema needs to be updated. Open emoncms in your browser and login with the admin user - this will be the first user you created. Then navigate to the Admin tab (top-right). Click 'Update & check' this will update your database. If the error prevents you from doing this, open index.php in a text editor and add the line: db_schema_setup(load_db_schema()); just above require("Modules/user/user_model.php"); If you go to emoncms again in your broser the error should now have disappeared. Remove the line once you have finished.


### Browser compatibility

**Chrome Ubuntu Linux -** works, no issues (this is the browser it is developed on)

**Firefox Ubuntu Linux -** works, no issues

**Internet explorer 9 Windows -** You may need to turn off compatibility mode to make it work, no issues with compatibility mode off.

**Chrome Windows -** works, no issues

**Chrome Mac -** ?

**Safari Mac -** ? dashboard + buggy?


