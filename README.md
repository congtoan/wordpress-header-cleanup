# WordPress Header Cleanup

Code snippets to remove unnecessary code from the WordPress header to improve performance and clean up the HTML output.

## Description

These code snippets remove various unnecessary meta tags, links, and scripts from the WordPress header to streamline your site's HTML output and potentially improve performance. The following elements are removed:

- Meta generator tags (WordPress and WooCommerce)
- EditURI/RSD link
- Windows Live Writer link
- Shortlinks
- Feed links (including comment feeds)
- Previous and Next post links
- REST API links
- oEmbed discovery links
- Emoji scripts and styles

## Usage

1. **Copy the Code:**
   - Copy the code snippets from `functions.php` and paste them into your child theme's `functions.php` file.
  ```php
  /* REMOVE UNNECESSARY WP HEAD */
  remove_action('wp_head', 'wp_generator');
  remove_action ('wp_head', 'rsd_link');
  remove_action( 'wp_head', 'wlwmanifest_link');
  remove_action( 'wp_head', 'wp_shortlink_wp_head');
  remove_action( 'wp_head', 'feed_links', 2 );
  remove_action( 'wp_head', 'feed_links_extra', 3 );
  remove_action( 'wp_head', 'adjacent_posts_rel_link', 10, 0 );
  remove_action( 'wp_head', 'adjacent_posts_rel_link_wp_head', 10, 0 );
  remove_action( 'wp_head', 'rest_output_link_wp_head' );
  remove_action( 'wp_head', 'wp_oembed_add_discovery_links' );
  remove_action( 'template_redirect', 'rest_output_link_header', 11, 0 );
  // Remove WP Emoji
  remove_action('wp_head', 'print_emoji_detection_script', 7);
  remove_action('wp_print_styles', 'print_emoji_styles');
  remove_action( 'admin_print_scripts', 'print_emoji_detection_script' );
  remove_action( 'admin_print_styles', 'print_emoji_styles' );
  ```

2. **Save and Upload:**
  - Save the changes and upload the functions.php file back to your child theme's directory.
    
3. **Verify:**
  - Visit your website and check the source code of your pages to ensure the unnecessary elements have been removed from the header.

## Code Explanation

Here is a detailed explanation of each code line included in the snippet:

```php
// Remove Meta Generator: <meta name="generator" content="WordPress x.x" /> 
// and <meta name="generator" content="WooCommerce x.x.x" />
remove_action('wp_head', 'wp_generator');

// Remove the EditURI/RSD
// Like: <link rel="EditURI" type="application/rsd+xml" title="RSD" href="http://localhost/wp/xmlrpc.php?rsd" />
remove_action('wp_head', 'rsd_link');

// Remove it if you don't know what is Windows Live Writer
// <link rel="wlwmanifest" type="application/wlwmanifest+xml" href="http://localhost/wp/wp-includes/wlwmanifest.xml" />
remove_action('wp_head', 'wlwmanifest_link');

// Remove page/post's short links
// Like: <link rel='shortlink' href='http://localhost/wp/?p=5' />
remove_action('wp_head', 'wp_shortlink_wp_head');

// Remove feed links
// Like: <link rel="alternate" type="application/rss+xml" title="WP Site &raquo; Feed" href="http://localhost/wp/feed/" />
remove_action('wp_head', 'feed_links', 2);

// Remove comment feeds
// Like: <link rel="alternate" type="application/rss+xml" title="WP Site &raquo; Comments Feed" href="http://localhost/wp/comments/feed/" />
remove_action('wp_head', 'feed_links_extra', 3);

// Remove PREV and NEXT links
// Like: <link rel='prev' title='The Post Before This One' href='http://localhost/wp/?p=4' />
remove_action('wp_head', 'adjacent_posts_rel_link', 10, 0);
remove_action('wp_head', 'adjacent_posts_rel_link_wp_head', 10, 0);

// Remove REST API links
// Like: <link rel='https://api.w.org/' href='http://localhost/wp-json/' />
remove_action('wp_head', 'rest_output_link_wp_head');
remove_action('template_redirect', 'rest_output_link_header', 11, 0);

// Remove oEmbed discovery links
// Like: <link rel="alternate" type="application/json+oembed" href="http://localhost/wp-json/oembed/1.0/embed?url=http%3A%2F%2Flocalhost%2Fwp%2F" />
remove_action('wp_head', 'wp_oembed_add_discovery_links');

// Remove WP Emoji scripts and styles
remove_action('wp_head', 'print_emoji_detection_script', 7);
remove_action('wp_print_styles', 'print_emoji_styles');
remove_action('admin_print_scripts', 'print_emoji_detection_script');
remove_action('admin_print_styles', 'print_emoji_styles');
```

## Contributing
Contributions are welcome! If you have any suggestions or improvements, please create a pull request or open an issue.
