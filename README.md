Forked From 
-----------
This is based on the Views Database Connector Module from:
https://www.drupal.org/project/views_database_connector

Clayfreeman came up with it and I stripped out everything except the MYSQL connector and then manually put in the links in the database tables.



TODO--- Re-write this section:


Installation
------------
Edit your sites settings.php file to include Move this directory into your Drupal module folder and enable it.

This is the default database connection that is in Drupal:
  $databases['default']['default'] = array(
     'driver' => 'mysql',
     'database' => '########',
     'username' => '########',
     'password' => '########',
     'host' => 'localhost',
     'prefix' => '',
   );

To allow the module to read you have add a second database connection.  Make sure the user has permission to read the AtoM sites database:
 $databases['atomDatabase']['default'] = array(
     'driver' => 'mysql',
     'database' => '########',
     'username' => '########',
     'password' => '########',
     'host' => 'localhost',
     'prefix' => '',
   );


Description
-----------
Views Database Connector is a powerful module that gives Views full access to
external database tables found in the settings for your Drupal installation.
With this module, you can setup a view around any table in any database
configuration. This can be extremely useful to pull external data from a
database to show to your users in a view.


Requirements and Limitations
----------------------------
This module depends on access to the information_schema table when using MySQL
or PostgreSQL. If using SQLite, access to the sqlite_master table is required.
These tables are used to gather information about your tables and their
respective column names and data types. If you cannot accommodate this
requirement, this module will not work. Also, any table names that conflict
with Drupal table names cannot be used, and any conflicting table names among
external databases will also need to be resolved. These restrictions are in
place because of the way that Views has structured the return value of its
hook_views_data() API.


Installation
------------
Upload this module's folder to your server and place it in the
sites/all/modules folder. In order to make use of this module, add extra
databases following the instructions found in the installation's
sites/default/settings.php file. After you've added a database or two, enable
the module. If you later decide to change your database configuration, it is
advisable to clear cache and cycle the module's state between disabled and
enabled.

We are using it to display an AtoM collection and have a sidebar module 
enabled as well.  This is just a JS picker that shows and hides two drupal 
attachments.  That script is in another module.  It is only needed for 
selecting between lists and not part of the core function.

Create a symbolic link to the themes folder (this is the link for our EJ Pratt 
Library connection).  This is only really for our theme, not needed.

sudo ln -s /var/www/drupal_pratt/sites/all/modules/custom/DrupalAtoMViewer/themeFiles/archives_view /var/www/drupal_pratt/sites/all/themes/pratt_green/

Utilization
-----------
When you add a new view, you should now be able to pick a new entry in the
"Show" select menu to use as the view type. Each item created by this module
will be prefixed by [VDC]. After you select one of these options and create
your view, the first column in the table will be added as the first field. You
should also be able to add the other columns as fields using the "Add" button.

Demo
----
I have exported our view that we use, it's not quite done yet, but you can load it if you are so inclined.  It is the Example.view.txt file and is not needed otherwise.


Issues
------

A bunch of theme overrides have been added to allow scraping of the AtoM site as well.  This has resulted in the module becoming more than the original intended use.