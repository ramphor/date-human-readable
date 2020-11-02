date-human-readable
===================

Generates human-readable strings for PHP DateTime objects. It handles dates in the past and future. For future dates, it uses the format 'In x unit', ie: 'In 1 minute'. For dates in the past, it uses 'x unit ago', ie: '2 years ago'.

Note: Comparison of dates, for those beyond a day apart, uses the difference between their Unix timestamps.

## Installation

If you're using Composer to manage dependencies, you can include the following
in your composer.json file:

```
"require": {
    "ramphor/date-human-readable": "~1.0.0"
}
```

Otherwise, you can simply require the file directly:

```php
require_once 'path/to/date-human-readable/src/HumanReadable.php';
```

## Usage

```php
use Ramphor\Date\HumanReadable;

HumanReadable::parse(new DateTime('now'));         // Moments ago
HumanReadable::parse(new DateTime('+ 59 second')); // Seconds from now
HumanReadable::parse(new DateTime('+ 1 minute'));  // In 1 minute
HumanReadable::parse(new DateTime('- 59 minute')); // 59 minutes ago

// You can supply a secondary argument to provide an alternate reference
// DateTime. The default is the current DateTime, ie: DateTime('now'). In
// addition, it takes into account the day of each DateTime. So in the next
// two examples, even though they're only a second apart, 'Yesterday' and
// 'Tomorrow' will be displayed

$now = new DateTime('1991-05-18 00:00:00 UTC');
$dateTime = new DateTime('1991-05-17 23:59:59 UTC');
HumanReadable::parse($dateTime, $now); // Yesterday

$now = new DateTime('1991-05-17 23:59:59 UTC');
$dateTime = new DateTime('1991-05-18 00:00:00 UTC');
HumanReadable::parse($dateTime, $now) // Tomorrow
```

## Tests

[![Build Status](https://travis-ci.org/ramphor/date-human-readable.png)](https://travis-ci.org/ramphor/date-human-readable)

From the project directory, tests can be ran using `phpunit`

## License

Released under the MIT License - see `LICENSE.txt` for details.
