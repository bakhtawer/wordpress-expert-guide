
# Creating Custom Post Types & Taxonomies in WordPress

Custom Post Types (CPTs) help organize your WordPress content beyond posts and pages.

## Creating a Custom Post Type

Add this to your theme’s `functions.php` or a custom plugin:

```php
add_action('init', function() {
  register_post_type('book', [
    'label' => 'Books',
    'public' => true,
    'has_archive' => true,
    'supports' => ['title', 'editor', 'thumbnail']
  ]);
});
```
Visit /book on your site to see the archive.
## Adding a Custom Taxonomy
Let’s register a “Genre” taxonomy for the “Books” CPT:
```
add_action('init', function() {
  register_taxonomy('genre', 'book', [
    'label' => 'Genres',
    'hierarchical' => true,
    'rewrite' => ['slug' => 'genre']
  ]);
});
```
## Benefits / Key Takeaways
- Cleanly separate and structure content types
- Improve user experience in WP admin
- Allow custom templates per content type
- Help with SEO and site scalability
