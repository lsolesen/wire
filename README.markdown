wire
==

A dependency injection container. Wire was originally developed by Troels Knak-Nielsen to use with [Konstrukt](http://konstrukt.dk/). In recent versions konstrukt is now relying heavily on dependency injection, and does not rely on wire anymore.

This makes it public as a standalone version of the code to be used in other applications.

Installation
--

	pear channel-discover pearhub.org
	pear install pearhub/wire

Example usage
--

	// an application will usually only have one version of wire
	$wire = new wire_Container();
	$wire->registerConstructor('pdo', create_function(
  		'$className, $args, $registry',
  		'return new pdoext_Connection("sqlite:../blog.sqlite", "root", "");'
	));
	
	$pdo = $wire->get('pdo);