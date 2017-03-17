[![Build Status](https://travis-ci.org/bu-ist/wp-unit-tests-essentials.svg?branch=master)](https://travis-ci.org/bu-ist/wp-unit-tests-essentials)
## Running Tests
1. Download https://github.com/bu-ist/wp-unit-tests-essentials/archive/master.zip
2. Copy everything but README & sample-plugin.php into your plugin/theme.
3. Update settings in the `tests/bootstrap.php` file to reflect your plugin/theme.
4. Write tests.
5. If this is not the first run,cleanup from the files and database from prior runs:
	```
    ls /tmp/wordpress*
    rm -fr /tmp/wordpress*
    echo "drop database wordpress_test" | mysql -u root
	```

6. Install WP tests:
	```
    bash bin/install-wp-tests.sh wordpress_test root '' localhost latest
	```

7. Run phpunit in the plugin’s root directory

	```
    phpunit
	```

## Trouble Shooting

If you run into problems with the `phpunit` command reporting that it's unable to connect to your database, it could be the case that php is tying to use a socket that isn't available. This can happen when you installed mysql with homebrew, while using the default php installation on OSX. To debug this a issue, run the following commands to figure out which socket php is trying to use, and which socket your mysql server is using.

```
php -i | fgrep 'mysql.default_socket'
mysql -e 'show variables where variable_name = "socket"'
```

One potential fix for this specific scenario is to symlink the php default socket to the one used by the homebrew's mysql server.

```
sudo ln -s /tmp/mysql.sock /var/mysql/mysql.sock
```
