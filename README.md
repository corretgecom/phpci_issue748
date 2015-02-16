# phpci_issue748
Dummy project to test issue 748 in PHPCI

## How it works
We have a basic build file that load a property file in **etc** folder.

PHPCI before 748 patch should crash because 

```
Buildfile: /build.xml
 [property] Loading /Volumes/develop/lab/phpci/etc/config.ini.dist
 [property] Unable to find property file: [PATH of PHPCI]/etc/config.ini.dist... skipped
```

It happens because the phing plugin doesn't change the current dir to the project dir and uses the PHPCI dir.

The patch 748 add an argument to phing to set the project dir, and then all relative paths' are working well.

```
 -Dproject.basedir="[Project base dir]" 
```

## How to test
In PHPCI Admin Options click on **Add Project**
and fill the fields:

**Where is your project hosted?**
GitHub

**Repository Name / URL (Remote) or Path (Local)**
corretgecom/phpci_issue748

**Project Title**
phpci_issue748

Save the Project and Build Now.

