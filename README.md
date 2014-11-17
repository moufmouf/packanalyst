Packanalyst
===========

A PHP package analyzer for Composer/Packagist.

Install
-------

Packanalyst requires a MongoDB database and an ElasticSearch database.

- Clone the application from the Git repository
- Run `composer.phar install`
- Configure the application in Mouf: `http://[yourserver]/[yourapp]/vendor/mouf/mouf`
- Init the databases: `./console.php reset`

Implementation details
----------------------

MongoDB item collection:

{
	"name": "FQDN",
	"inherits": [ FQDN1, FQDN2... ],
	"globalInherits": [ FQDN1, FQDN2... ], // inherits + inherits of parents, recursively
	"type": "class",
	"packageName": "packagename",
	"packageVersion": "version",
	"phpDoc": "doc class",
	"refresh": bool // Set to true to force refresh
}

index on: packageName + packageVersion
index on: name
index on: inherits
index on: globalInherits

MongoDB package collection:

{
	packageName: ""
	version: ""
	type: ""
	releaseDate: date
	downloads: int
	favers: int
}

Packanayst use Grunt
-------------------------
Here is the documentation : [Grunt documentation](http://gruntjs.com/)

Quick use :
1. First install NodeJS and add it to your PATH
2. Go to `src/views`, here are your `Gruntfile.js` & `package.json`. Download your depencies by using command : `npm install`
3. Now you can use grunt by using `grunt` or `grunt dev`