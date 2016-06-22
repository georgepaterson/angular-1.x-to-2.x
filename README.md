# Migrating Angular 1.x applications to 2.x

The Angular team have defined an upgrade path for existing Angular 1 applications https://angular.io/docs/ts/latest/guide/upgrade.html. 

The migration can be achieved incrementally using the Angular upgrade module to either upgrade Angular 1 modules to Angular 2 or downgrade Angular 2 modules to Angular 1.

To be able to upgrade or downgrade components it is necessary that the component conforms to certain code styles https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md. The Rule of 1 https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#style-y001, folders by feature https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#folders-by-feature-structure, and modularity rules https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#modularity. With the application structured in a modular styles it enables the application to be upgraded one module at a time.

Using the Angular 1 style rules also enables comprehensive unit testing, the Angular 1 unit tests can be used in the Angular 2 application.

## Module loading

Using Angular modularity rules the application would have a number of smaller JAvaScript files to load. In Angular 1 builds this may have been maintained with Grunt/Gulp and Bower.

For instance Yeoman would prepare a rewrite based on files in an assets folder and injected them in to the index file in certain comment blocks. 

	<!-- bower:js -->
	
	<!-- endbower -->
	<!-- endbuild -->
	<!-- build:js({.tmp,app}) scripts/scripts.js -->
	
	<!-- endbuild -->
	
While Bower is a useful package manager, npm also maintains the majority of the same browser ready packages, eliminating the requirement for Bower.

The Grunt build process can also be replaced by a dedicated modules loader suchs as SystemJS https://github.com/systemjs/systemjs or Webpack http://webpack.github.io/. Angular 2 uses SystemJS be default. Angular 1 applications can use a module loader now in preparation for Angular 2 migration.
	
	

 

 
