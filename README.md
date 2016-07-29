[![Build Status](https://travis-ci.org/bu-ist/wp-unit-tests-essentials.svg?branch=master)](https://travis-ci.org/bu-ist/wp-unit-tests-essentials)
##Running Tests##
1. Download https://github.com/bu-ist/wp-unit-tests-essentials/archive/master.zip
2. Copy everything but README & sample-plugin.php into your plugin/theme.
3. Update settings in the `tests/bootstrap.php` file to reflect your plugin/theme.
4. Write tests.
5. (if not 1st run) Cleanup from prior runs:     
	```bash
ls /tmp/wordpress* 
rm -fr /tmp/wordpress*
echo "drop database wordpress_test" | mysql
	```
	
5. Install WP tests:
	```bash
bash bin/install-wp-tests.sh wordpress_test root '' localhost latest
	```
	
6. Run phpunit the plugin’s root directory

	```bash
phpunit
	```
