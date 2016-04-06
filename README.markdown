wire [![Build Status](https://secure.travis-ci.org/lsolesen/wire.png?branch=master)](http://travis-ci.org/lsolesen/wire)
==

A dependency injection container. Wire was originally developed by Troels Knak-Nielsen to use with [Konstrukt](http://konstrukt.dk/). In recent versions konstrukt is now relying heavily on dependency injection, and does not rely on wire anymore.

This makes it public as a standalone version of the code to be used in other applications.

Installation
--

The easiest way to install Konstrukt, is through Composer. Add the following to your `composer.json`:

    {
      "repositories": [
        {
          "type": "git",
          "url": "https://github.com/lsolesen/wire.git"
        }
      ],
      "minimum-stability": "dev",
      "require": {
        "troelskn/wire": "*"
      }
    }

Example usage
--

	// an application will usually only have one version of wire
	$wire = new wire_Container();
	$wire->registerConstructor('pdo', create_function(
  		'$className, $args, $registry',
  		'return new pdoext_Connection("sqlite:../blog.sqlite", "root", "");'
	));

	$pdo = $wire->get('pdo);