![Cat In Black Meteor](http://res.cloudinary.com/czarny-kod/image/upload/v1467275882/meteor_mfdvco.jpg)
#Cat In Black
From the beginning, we have done successfully more than 300 projects for companies from different sectors. We create startups, we precursors and love Lean Startup methodology and Customer Development. We know many of the technologies and know which one will be the most right for you.

Read more about company: https://catin.black and our Meteor Partnership: http://catin.black/meteor 

## Meteor Starter Pack for Apps
To fully use the module system and ensure that our code only runs when we ask it to, we recommend that all of your application code should be placed inside the imports/ directory. This means that the Meteor build system will only bundle and include that file if it is referenced from another file using an import (also called “lazy evaluation or loading”).

Meteor will load all files outside of any directory named imports/ in the application using the default file load order rules (also called “eager evaluation or loading”). It is recommended that you create exactly two eagerly loaded files, client/main.js and server/main.js, in order to define explicit entry points for both the client and the server. Meteor ensures that any file in any directory named server/ will only be available on the server, and likewise for files in any directory named client/. This also precludes trying to import a file to be used on the server from any directory named client/ even if it is nested in an imports/ directory and vice versa for importing client files from server/.

These main.js files won’t do anything themselves, but they should import some startup modules which will run immediately, on client and server respectively, when the app loads. These modules should do any configuration necessary for the packages you are using in your app, and import the rest of your app’s code.


## Structure
### APP
```
imports/
	client/
		main.js                 # import client startup through a single index entry point
		lib/
			routes.js 			# set up all routes in the app
		utils/
			functions.js
			helpers.js
		views/
			pages/
				home/	
					home.js
					home.jade
			partials/
				footer/	
					footer.js
					footer.jade
				header/	
					header.js
					header.jade

server/
  main.js 						# import server startup through a single index entry point

client/
  main.js                       # client entry point, imports all client code
  main.jade

lib/
	main.js 					# lib entry point, imports all lib code

```
### Deploy
Using MUPX - https://github.com/arunoda/meteor-up/tree/mupx
npm install mupx -g

#### Development server
For example if you are using: http://meteor.toys you will be able to use Mongol in your browser. 
It is a good idea to use: ```jabbslad:basic-auth``` and set password when using this deploy version. Use it on your server site code:
```

if (process.env.NODE_ENV === "development") {
	var basicAuth = new HttpBasicAuth("catinblack-login", "catinblack-password");
	basicAuth.protect();
	METEORTOYSSHELL = true;
}

```

Structure:

```

devel/
	mupx.json 						# Meteor Up configuration file
	settings.json 					# Settings for Meteor's settings API

```

#### Production server
Structure:

```

production/
	mupx.json 						# Meteor Up configuration file
	settings.json 					# Settings for Meteor's settings API

```

## Packages
```
meteor-base             # Packages every Meteor app needs to have
mobile-experience       # Packages for a great mobile UX
mongo                   # The database Meteor supports right now
blaze-html-templates    # Compile .html files into Meteor Blaze views
reactive-var            # Reactive variable for tracker
jquery                  # Helpful client-side library
tracker                 # Meteor's client-side reactive programming library

standard-minifier-css   # CSS minifier run for production mode
standard-minifier-js    # JS minifier run for production mode
es5-shim                # ECMAScript 5 compatibility for older browsers.
ecmascript              # Enable ECMAScript2015+ syntax in app code

iron:router
mquandalle:jade
fourseven:scss
aldeed:simple-schema
aldeed:autoform
check
accounts-base
```

## Motivation

Fast start new project

## Installation

```
> meteor npm install
> meteor --settings settings.json
```

## Tests

```
meteor test --driver-package=practicalmeteor:mocha --full-app --settings settings.json
```

### Simple test

This loads your application in a special “test mode”. What this does is:
Doesn’t eagerly load any of our application code as Meteor normally would.
Does eagerly load any file in our application (including in imports/ folders) that look like *.test[s].*, or *.spec[s].*
Sets the Meteor.isTest flag to be true.
Starts up the test driver package (see below).

### --full-app

It loads test files matching *.app-test[s].* and *.app-spec[s].*.
It does eagerly load our application code as Meteor normally would.
Sets the Meteor.isAppTest flag to be true (instead of the Meteor.isTest flag).

