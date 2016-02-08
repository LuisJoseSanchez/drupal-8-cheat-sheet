# Drupal 8 Cheat Sheet

## Drupal 8 Installation

This installation has been tested in **Ubuntu 15.10**

### Install `drush`

If you don't have `drush` installed, type the following:

```console
sudo apt-get install composer
composer global require drush/drush
```

Edit the file `.profile` and add the following line:

```console
PATH="$HOME/.composer/vendor/bin:$PATH"
```

Resource the new configuration:

```console
source ~/.profile
```

Check the installation:

```console
drush status
```

### Create `MySQL` database

Create database with name `mydrupal8`. Remember to enter the MySQL root password when you are prompted, not the system password.

```console
mysql -u root -p -e "CREATE DATABASE mydrupal8"
```

### Download Drupal 8

```console
sudo chmod a+w /var/www/html/
cd /var/www/html/
drush dl drupal
mv drupal-8.0.3 mydrupal8
```

### Install Drupal 8

```console
cd /var/www/html/mydrupal8/
drush si standard --db-url=mysql://root:root@localhost/mydrupal8 --account-name="admin" --account-pass="123456" --account-mail="chiquito@condemor.com"
cd sites/default/
sudo cp ../example.settings.local.php ./settings.local.php
sudo cp default.settings.php settings.php
sudo cp default.services.yml services.yml
sudo chmod 0666 settings.php services.yml
sudo chown myuser:www-data files
```

Now go to <http://localhost/mydrupal8/> and enter as administrator with user `admin` and password `123456`.

