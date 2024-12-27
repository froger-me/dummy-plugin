# WP Package Updater - Plugins and themes update library

### Description

Used to enable updates for plugins and themes distributed via WP Packages Update Server.

### Requirements

The library must sit in a `lib` folder at the root of the plugin or theme directory.
A file `wppus.json` must be present in the root of the plugin or theme directory.


Before deploying the plugin or theme, make sure to change the `$prefix_updater` with your plugin or theme prefix.

Before deploying the plugin or theme, make sure to change the following value in `wppus.json`:
- `server`          => The URL of the server where WP Packages Update Server is installed ; **required**
- `requireLicense`  => Whether the package requires a license ; `true` or `false` ; optional

### Code to include in main plugin file or functions.php

```php
require_once __DIR__ . '/lib/wp-package-updater/class-wp-package-updater.php';

$prefix_updater = new WP_Package_Updater(
	wp_normalize_path( __FILE__ ),
	0 === strpos( __DIR__, WP_PLUGIN_DIR ) ? wp_normalize_path( __DIR__ ) : get_stylesheet_directory()
);
```

### Content of `wppus.json`

```json
{
   "server": "https://server.domain.tld/",
   "requireLicense": false
}
```