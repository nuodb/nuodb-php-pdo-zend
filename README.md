# Zend Framework Data Adapter for NuoDB #

NuoDB supports both Zend Framework version 1 and 2.
Customers should download the Zend Framework from the Zend website: framework.zend.com.

For Zend Framework v1, we provide Zend Framework v1 Data Adapter.  This adapter is developed and tested with the Zend Framework Version 1.11.12 & 1.12.3.  The NuoDB ZF1 Data Adapter depends on the NuoDB PHP PDO driver.  The NuoDB PHP PDO driver must be installed and configured before using the NuoDB Zend Framework v1 Data Adapter.

For Zend Framework v2, no adapter is necessary.  The existing NuoDB PHP PDO driver works with the Zend Framework v2.  

## PREREQUISITES ##

Both Zend Framework v1 and v2 depend on the NuoDB PHP PDO Driver.  The NuoDB PHP PDO Driver is provided in the NuoDB install in the 'drivers/php_pdo' directory. Follow the instructions to install/configure/test the NuoDB PHP PDO Driver before attempting to use the Zend Framework.

PHP installation that conforms to the PHP API version 20090626.
NuoDB PHP PDO Driver extension that is installed and configured.
Zend Framework Version 1 or 2.


## BUILDING ##

The NuoDB Zend Framework v1 Data Adapter for NuoDB is delivered as PHP source code, so there is nothing to build.


## INSTALL ##

To install the NuoDB Zend Framework v1 Data Adapter, copy the file Nuodb.php to your Zend Framework v1 library/Zend/Db/Adapter/Pdo directory.


## QUICK START ##

There is two examples, one for each Zend Framework: 

nuodb_zf1_quickstart.tar.gz 
nuodb_zf2_tutorial.tar.gz

There is a third example in the zf_hockey directory.  The zf_hockey example is deprecated and will be removed in a future version of NuoDB.


## LICENSE ##

This module is released under the [NUODB License] [license].

Related Pages:

[homepage]: http://www.nuodb.com
[license]: https://github.com/nuodb/nuodb-drivers/blob/master/LICENSE

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/f0b9c0e53893cfe6ef51b166d569a5d5 "githalytics.com")](http://githalytics.com/nuodb/nuodb-php-pdo-zend)
