# A Library of Collections

[![Build Status](https://travis-ci.org/morrisonlevi/Ardent.svg?branch=gcl)](https://travis-ci.org/morrisonlevi/Ardent)

Arrays in PHP are useful but sometimes stronger type guarantees are needed or wanted. This library hopes to fill the gap.

This is the general idea:

```php
// include src/ardent.php or composer's autoloader

use morrisonlevi\ardent\{
  function int_t,
  function nullable_t,
  function string_t,
  dict,
  vec
};

// Represents vec<int>.
$vec = vec::of(int_t());

// Okay, all values are ints.
$vec->append(1, 3, 7);

// Possibly a type-error, depending on your assertion settings.
//$vec[0] = 'Not an int';

// Represents dict<string, ?int>.
$dict = dict::of(string_t(), nullable_t(int_t()));
// dict optionally takes 2 optional functions for hashing and equality.

// These are good.
$dict['one'] = 1;
$dict['null'] = null;

// Possibly type-errors, depending on your assertion settings.
//$dict[true] = 1;
//$dict['float'] = 1.6;

// use class_t(ClassName::class) for classes and interfaces
```

### Requirements

  - Patience. This project is unstable and subject to significant changes from release to release.
  - PHP 7.0.

### Roadmap

There is no official roadmap for this project. I intend to release version 1.0.0 when I am confident enough in the API that it is suitable for public use. Until then, minor versions will be tagged as they are deemed helpful.

### How can I help?

The best way to help is to use the library (at your own risk) and [submit issues](https://github.com/morrisonlevi/Ardent/issues) when you find them. Over 99% of the library has been executed in a unit test but the quality of some of these tests is poor; improved tests are definitely welcome.

##### Can you add X structure?

Maybe. Open an issue and I'll look into it. 

### Why not use the existing Standard PHP Library?

The Standard PHP Library (SPL) has many problems, some of which are documented in an [unfinished RFC regarding the SPL](https://wiki.php.net/rfc/spl-improvements). I won't go into full details here, but essentially the SPL is not providing the standardized data structures and algorithms that I feel the PHP community needs.

### What's up with the name?

This project was originally aimed to fix the SPL; as such I had named it SPL. Eventually I realized that I would do better with a different name; I picked Ardent it describes how I feel about the need for this kind of library. Unfortunately another PHP project decided to use the name after I had already picked it.
