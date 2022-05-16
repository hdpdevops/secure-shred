# secure-shred

Safely deletes files

## Requirements
PHP >= 7.1 (PHP >= 5.4 is supported but requires `paragonie/random_compat`)

## Installation

composer.json

```javascript
{
	"require": {
		"hdpdevops/secure-shred": "^1"
	},
	"repositories": [
        {
            "type": "git",
            "url": "https://github.com/hdpdevops/secure-shred.git"
        }
}
```

Run `composer install` or `composer require hdpdevops/secure-shred`

## Usage
```php
// load autoload composer
require 'vendor/autoload.php';

$shred = new Shred\Shred($n); // $n (optional) <= Number of iterations. Default 3.

$shred->shred('folder/file.txt'); // <= Overwrite and remove.
$shred->shred('folder/file.txt', false); // <= Only overwrite.

// Check if remove
if ($shred->shred('folder/file.txt')) {
	// The file is truncated & removed.
} else {
	// Impossible to overwrite or remove the file. See filepath & file permissions.
}
```

secure-shred overwrites 'n' times the file for making it more difficult to recover (Imposible is nothing!). Obviously inspired by shred for linux.
If you want to delete large files, or repeat a large number of times this will increase the execution time of the script.

```php
ini_get('max_execution_time'); // Max execution script time in seconds.
set_time_limit($s); // $s => Set max time limit in seconds.
```

## Credits
secure-shred is based on Shred PHP which was created by Dani C.

Released under the MIT license.
