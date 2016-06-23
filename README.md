# Migrating Angular 1.x applications to 2.x

The Angular team have defined an upgrade path for existing [Angular 1 applications](https://angular.io/docs/ts/latest/guide/upgrade.html). 

The migration can be achieved incrementally using the Angular upgrade module to either upgrade Angular 1 modules to Angular 2 or downgrade Angular 2 modules to Angular 1.

To be able to upgrade or downgrade components it is necessary that the component conforms to certain [code styles](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md) . The [Rule of 1](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#style-y001)  , [folders by feature](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#folders-by-feature-structure), and [modularity rules](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#modularity) are core to the migration process. If the application conforms to the good practices defined in the code styles guide it should be possible to migrate the application successfully.

Where the Angular code styles have been implemented, the seperation of concerns should support automated unit testing through frameworks such as Jasmine. Unit testing should continue through to the migrated application supported the developer during the build.

## Module loading

Using Angular modularity rules the application would have a number of smaller JavaScript files to load. In Angular 1 builds this may have been maintained with Grunt/Gulp and Bower.

For instance Yeoman would prepare a rewrite based on files in an assets folder and injected them in to the index file in certain comment blocks. 

	<!-- bower:js -->
	
	<!-- endbower -->
	<!-- endbuild -->
	<!-- build:js({.tmp,app}) scripts/scripts.js -->
	
	<!-- endbuild -->
	
While Bower is a useful package manager, npm also maintains the majority of the same browser ready packages, eliminating the requirement for Bower.

The Grunt build process can also be replaced by a dedicated modules loader suchs as [SystemJS](https://github.com/systemjs/systemjs) or [Webpack](http://webpack.github.io/). Angular 2 uses SystemJS be default.

It is recommended Angular 1 applications begin using a module loader now in preparation for Angular 2 migration.

## Components

Component directives were introduced in Angular 1.5, they are directives that define their own templates, controllers and bindings. Component directives became components in Angular 2, for a component directive to be upgraded to a component they require the following properties.
	
	restrict: 'E'
	scope: {}
	bindToController: {}
	controllerAs
	template or templateUrl

Component directives may use:	
	
	transclude (optional)
	require (optional)
	
Component directives may not use:

	compile
	replace: true
	priority/terminal

## Services

Services effectively remain the same 

## Controllers

Components in Angular 2 define their own controllers removing the requirement for an independant controller.

## $scope

Components define scope, the $scope attribute has been removed.

## Styles

The link tag used in the index page is still used in Angular 1 and 2. Angular 2 adds a styleUrls property to components allowing it to define a style sheet.

	styleUrls: ['app/movie-list.component.css'], 
	
## Filters

Filters in Angular 1 effectively become Pipes in Angular 2. Filters that don't become Pipes could alternatively be coded as components.

## Summary

## References 
