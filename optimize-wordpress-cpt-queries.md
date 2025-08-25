# Optimizing WordPress Custom Post Type (CPT) Queries for Performance

When working with large Custom Post Types in WordPress, database queries — especially `meta_query()`,
can become very slow because of how WordPress stores metadata in the `wp_postmeta` table.

This guide demonstrates how to optimize CPT performance using indexes and query optimization techniques.

---

## Why CPTs Become Slow

WordPress stores all custom field values (meta) in `wp_postmeta`.  
When we write meta queries like:

```php
$args = [
    'post_type'  => 'car',
    'meta_query' => [
        [
            'key'   => 'price',
            'value' => 200000,
            'compare' => '>=',
            'type' => 'NUMERIC'
        ]
    ]
];
$query = new WP_Query($args);
```

WordPress creates heavy JOIN queries between wp_posts and wp_postmeta.
As the table grows into 100,000+ rows, performance drops.

## Tip 1: Add Indexes to wp_postmeta
By default, meta_key and meta_value are not indexed!
Use this SQL once (via phpMyAdmin or SSH)
```
ALTER TABLE wp_postmeta
  ADD INDEX `meta_key` (`meta_key`(191)),
  ADD INDEX `meta_value` (`meta_value`(191));
```
