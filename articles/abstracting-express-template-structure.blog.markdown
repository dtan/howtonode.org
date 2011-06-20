Title: Abstracting Express Template Structure
Author: Dale Tan
Date: Mon Jun 20 2011 02:19 GMT-0500 (EST)

While trying to learn Node.js, I decided to just jump right in and start with the suped up version of the Express MVC example modified by [cliftonc][mvc].  I'm definitely no expert on the MVC pattern (a novice, really), but I know that I do like to keep structure to my templates, regardless of what I'm using.  Since Express supports five templating languages by default (and not to mention you can add others of your choice), it only makes sense to organize your `Views` by their language.  This will keep a nice, tidy templates structure.  

Being the cache junkie I am, I like to create variables for EVERYTHING if it's going to be repeated on the page even just twice.  It makes it easier to change it in one spot in the long run anyway, right?  Not only that, but having your variables set up top also makes it easier to know WHERE to make certain changes.  With that being said, my first foray into the Express framework, one of the first things I did was define my `views` and `view engine` into variables a the top of my file.  Instead of this:

	// somewhere in the middle of the page
	app.set('views', __dirname + '/views/');
	app.set('view engine', 'jade');
  
I extracted those two values and defined them at the top of my file:

	var templateEngine = 'jade',
		templatesPath  = __dirname + '/views/' + templateEngine;
	// some other code before defining the views and view engine
	app.set('views', templatesPath);
	app.set('view engine', templateEngine);

This looks good and dandy at face value.  Now, I forgot to mention that within my `templatesPath` folder, I kept with the naming convention that express ships with by default: `layout.{ext}` and `index.{ext}`.  So in my case `layout.jade` and `index.jade` where the `layout` is the entire template structure.

[mvc]: https://github.com/cliftonc/express-mvc-bootstrap
