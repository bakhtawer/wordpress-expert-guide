# Hooks in WordPress — Actions vs Filters

WordPress is highly extensible because of **Hooks**, which let developers insert custom functionality into core processes without modifying core files.

There are two main types of hooks:
- **Actions** — Let you add or execute custom code at a specific point.
- **Filters** — Let you modify data before it’s output or saved.

---

## 1. **Actions in WordPress**
**Actions** are triggered at specific points in WordPress execution.  
You use `add_action()` to run your function when that point is reached.

**Syntax:**
```php
add_action( $hook_name, $callback_function, $priority, $accepted_args );
```
## Example — Adding a Custom Message to the WordPress Login Page
```
<?php
// Add a custom message above the login form
function my_custom_login_message() {
    echo '<p style="text-align:center; color:#2271b1; font-weight:bold;">Welcome! Please log in securely.</p>';
}
add_action( 'login_message', 'my_custom_login_message' );
```
## How to test:
-Add this code to your theme’s functions.php file (or a custom plugin).
-Go to your WordPress login page (/wp-login.php).
-You’ll see a custom message above the login form.

## Filters in WordPress
Filters allow you to modify or replace data before it is displayed or saved.
You use add_filter() to intercept and change that data.
```
add_filter( $hook_name, $callback_function, $priority, $accepted_args );

```
# Example — Changing the WordPress Login Logo URL
```
<?php
// Change the logo link to your own website
function my_custom_login_logo_url( $url ) {
    return 'https://example.com';
}
add_filter( 'login_headerurl', 'my_custom_login_logo_url' );
```
# How to Test ?
- Add this code to your theme’s functions.php.
- Visit /wp-login.php.
- Click the WordPress logo — it now goes to your site instead of wordpress.org.


