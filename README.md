<img src="http://52.48.57.141/php-actions.png" align="right" alt="PHP Actions for Github" />

Run your PHPUnit tests in your Github Actions.
==============================================

PHPUnit is a programmer-oriented testing framework for PHP.
It is an instance of the xUnit architecture for unit testing frameworks.

**Please note that PHPUnit v5 is no longer supported, and neither is PHP v5.*! Please upgrade to a newer version (see https://phpunit.de/getting-started/phpunit-5.html)**

Usage
-----

Create your Github Workflow configuration in `.github/workflows/ci.yml` or similar.

```yaml
name: CI

on: [push]

jobs:
  build-test:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - uses: php-actions/composer@v1 # or alternative dependency management
    - uses: php-actions/phpunit@v5
    # ... then your own project steps ...
```

Example
-------

We've put together an extremely simple example application that uses `php-actions/phpunit`. Check it out here: https://github.com/php-actions/example-phpunit.

Inputs
------

The following configuration options are available:

+ `config` Path to the `phpunit.xml` file (default: `test/phpunit/phpunit.xml`)
+ `junit` Path to junit output file (default: `test/phpunit/_junit/junit.xml`)
+ `memory` The memory limit to run your tests with (default: `512M`)
+ `bootstrap` The path to the bootstrap file (default: `vendor/autoload.php`)

The syntax for passing in a custom input is the following:

```yaml
...

jobs:
  unit-tests:

    ...

    - name: PHPUnit tests
      uses: php-actions/phpunit@v5
      with:
        configuration: custom/path/to/phpunit.xml
        memory_limit: 256M
```

If you require other configurations of phpunit, please request them in the [Github issue tracker](https://github.com/php-actions/phpunit/issues)

Versions
--------

The Github Actions version numbers are in sync with the PHPUnit version. This allows you to specify which version of PHPUnit your project should run by using the @ syntax.

Current versions supported by this Action:

+ 9.*
+ 8.*

Please note **the version number of the Github Action must match your composer.json major version number**. For example, if your composer.json requires `phpunit/phpunit 8.5.8`, you must use `php-actions/phpunit@v8`, as major versions of PHPUnit are incompatible with each other.  

If you require a specific version that is not listed here, please request them in the [Github issue tracker](https://github.com/php-actions/phpunit/issues)

***

If you found this repository helpful, please consider [sponsoring the developer][sponsor].

[sponsor]: https://github.com/sponsors/g105b