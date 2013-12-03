# Zend Framework Data Adapter for NuoDB #

NuoDB supports both Zend Framework version 1 (ZF1) and 2 (ZF2).  Customers can download the Zend Framework from the Zend website: framework.zend.com.

For Zend Framework v1, we provide a Zend Framework v1 Data Adapter.  This adapter is developed and tested with the Zend Framework Versions 1.11.12 & 1.12.3.  The NuoDB ZF1 Data Adapter uses the NuoDB PHP PDO driver.  The NuoDB PHP PDO driver must be installed and configured before using the NuoDB Zend Framework v1 Data Adapter.

For Zend Framework v2, no adapter is necessary.  The existing NuoDB PHP PDO driver works with the Zend Framework v2.  

## PREREQUISITES ##

Both Zend Framework v1 and v2 depend on the NuoDB PHP PDO Driver.  The NuoDB PHP PDO Driver is provided by the NuoDB installation in the 'drivers/php_pdo' directory. Follow the instructions to install/configure/test the NuoDB PHP PDO Driver before attempting to use the Zend Framework.


## BUILDING ##

The NuoDB Zend Framework v1 Data Adapter is distributed as PHP source code, so there is nothing to build.


## INSTALL ##

Install, configure, and test the NuoDB PHP PDO Driver.

For Zend Framework 1, to install the NuoDB Zend Framework v1 Data Adapter, copy the file Nuodb.php to your Zend Framework v1 library/Zend/Db/Adapter/Pdo directory.


## QUICK START ##

There are two examples provided in this directory, one for each Zend Framework: 

nuodb_zf1_quickstart.tar.gz 
nuodb_zf2_tutorial.tar.gz

Zend Framework v1 quickstart
----------------------------
There is a quickstart example on the framework.zend.com website.  The instructions for the quickstart in the Zend Framework v1 documenation. The quickstart is simple virtual guestbook application where visitors to a website can sign a guestbook.  

Follow the instructions for the quickstart example: 

  http://framework.zend.com/manual/1.12/en/learning.quickstart.html

Instead of using sqlite.  Configure the NuoDB Zend Framework v1 Data Adapter as follows:

zf.sh configure db-adapter 'adapter=PDO_NUODB&host=localhost&username=cloud&password=user&dbname=test@localhost&schema=guestbook&options.autoQuoteIdentifers=false' production

Start the NuoDB Storage Manager (SM) an Transaction Engine (TE) on test@localhost, then use the following nuosql command to create the schema, table, and data:

nuosql test@localhost --user cloud --password user
> DROP SCHEMA guestbook CASCADE IF EXISTS;
> CREATE SCHEMA guestbook;
> USE guestbook;
> CREATE TABLE guestbook (
    "id" INTEGER NOT NULL GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "email" VARCHAR(32) NOT NULL DEFAULT 'noemail@test.com',
    "comment" TEXT NULL,
    "created" DATETIME NOT NULL
);
> INSERT INTO guestbook ("email", "comment", "created") VALUES
    ('ralph.schindler@zend.com',
    'Hello! Hope you enjoy this sample zf application!',
    NOW());
> INSERT INTO guestbook ("email", "comment", "created") VALUES
    ('foo@bar.com',
    'Baz baz baz, baz baz Baz baz baz - baz baz baz.',
    NOW());
> 

Source code for the complete guestbook application is contained in nuodb_zf1_quickstart.tar.gz.



Zend Framework v2 tutorial
---------------------------
There is a tutorial example on the framework.zend.com website.  The instructions for the tutorial in the Zend Framework v2 documenation. The tutorial is a simple inventory system to track music albums.

Follow the instructions for the tutorial example: 

  http://framework.zend.com/manual/2.2/en/user-guide/overview.html#the-tutorial-application

Instead of using MySQL, start the NuoDB Storage Manager (SM) an Transaction Engine (TE) on test@localhost, then use the following nuosql command to create the schema, table, and data:

nuosql test@localhost --user cloud --password user
SQL> DROP SCHEMA zf2tutorial CASCADE IF EXISTS;
SQL> CREATE SCHEMA zf2tutorial;
SQL> USE zf2tutorial;
SQL> CREATE TABLE "album" (
  "id" int NOT NULL generated by default as identity,
  "artist" varchar(100) NOT NULL,
  "title" varchar(100) NOT NULL,
  PRIMARY KEY (id)
);
SQL> INSERT INTO album (artist, title)
    VALUES  ('The  Military  Wives',  'In  My  Dreams');
SQL> INSERT INTO album (artist, title)
    VALUES  ('Adele',  '21');
SQL> INSERT INTO album (artist, title)
    VALUES  ('Bruce  Springsteen',  'Wrecking Ball (Deluxe)');
SQL> INSERT INTO album (artist, title)
    VALUES  ('Lana  Del  Rey',  'Born  To  Die');
SQL> INSERT INTO album (artist, title)
    VALUES  ('Gotye',  'Making  Mirrors');

The NuoDB connection settings should be placed in config/autoload/global.php as follows:

<?php
return array(
    'db' => array(
        'driver'         => 'Pdo',
        'dsn'            => 'nuodb:database=test@localhost;schema=zf2tutorial',
        ),
    'service_manager' => array(
        'factories' => array(
            'Zend\Db\Adapter\Adapter'
                    => 'Zend\Db\Adapter\AdapterServiceFactory',
        ),
    ),
);

The NuoDB username and password should be stored in config/autoload/local.php as follows:

<?php
return array(
    'db' => array(
        'username' => 'cloud',
        'password' => 'user',
    ),
);

Source code for the complete tutorial application is contained in nuodb_zf2_tutorial.tar.gz.


zf_hockey is deprecated
-----------------------
There is a third example in the zf_hockey directory.  The zf_hockey example is deprecated and will be removed in a future version of NuoDB.


## LICENSE ##

This module is released under the [NUODB License] [license].

Related Pages:

[homepage]: http://www.nuodb.com
[license]: https://github.com/nuodb/nuodb-drivers/blob/master/LICENSE

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/f0b9c0e53893cfe6ef51b166d569a5d5 "githalytics.com")](http://githalytics.com/nuodb/nuodb-php-pdo-zend)