## How do you fix the White Screen of Death?
Here are several possible steps we can follow to debug and resolve the problem 
# 1. Enable debugging in wp-config.php:
```
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
```
# 2. Disable all plugins, switch to the default theme.
 - Check one by one and disable themes and plugins.
 - Remove inactive Plugins
 - Switch to the default theme
# 3. Increase PHP memory limit:
```
define('WP_MEMORY_LIMIT', '256M');
```
Adding this to your wp-config.php file helps prevent and fix the White Screen of Death (WSOD) in WordPress by 
increasing the amount of memory PHP can use to run your site.
# Why does it works?
The WSOD often happens when:
- A plugin or theme consumes too much memory.
- PHP runs out of memory before completing a task.
- No error is shown—just a blank screen.

