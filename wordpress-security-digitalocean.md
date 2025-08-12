
# Securing WordPress on DigitalOcean: A Complete Guide

WordPress on a cloud server gives you power—but you need to secure it.

## 1. Update Everything

Always update WordPress core, plugins, and themes.

## 2. Use Nonces for Form Security

```php
if (!isset($_POST['my_nonce']) || !wp_verify_nonce($_POST['my_nonce'], 'my_action')) {
  die('Security check failed');
}
```
## Disable XML-RPC
```
add_filter('xmlrpc_enabled', '__return_false');
```
## Harden File Permissions
```
find /var/www/html -type d -exec chmod 755 {} \;
find /var/www/html -type f -exec chmod 644 {} \;
```
## Enable SSL with Let’s Encrypt
If using Nginx:
```
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```
