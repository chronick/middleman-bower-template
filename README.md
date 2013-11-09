#Headcanon's HTML5 Middleman + Bower template
This is a (somewhat opinionated) [Middleman](http://middlemanapp.com) template I made to help speed up static site building. It encourages asset management with [Bower](http://github.com/twitter/bower) and includes a default bower.json. This template also makes it easy to add [Typekit](http://typekit.com) and [Google Analytics](http://google.com/analytics) to your site. 

a lot of credit goes to [Danny Prose's Middleman HTML5BP-HAML](https://github.com/dannyprose/Middleman-HTML5BP-HAML) template, as well as the general [HTML5 Boilerplate](http://html5boilerplate.com) for helping me make this template.

This bad boy is distributed under the MIT license.


##Features:
* [Markdown](http://daringfireball.net/projects/markdown/) rendering
* [SCSS](http://sass-lang.com)
* [Coffeescript](http://coffeescript.org)
* a [Favicon Maker](http://github.com/follmann/middleman-favicon-maker)
* Middleman [Live Reload](http://github.com/middleman/middleman-livereload)
* [Modernizr](http://modernizr.com)
* [Normalize.css](http://necolas.github.com/normalize.css) 
* [Bower](http://github.com/twitter/bower) package management
* A Gemfile.ru for easy Heroku deployment
* A [middleman-deploy](http://github.com/tvaughan/middleman-deploy) config snippet to ease FTP deployment


##Installation
1. Download/clone to: `~/.middleman/html5bower`
2. Create your new Middleman project: `middleman init my_new_project --template=html5bower`
3. `bower install` to install the assets in the `components/` directory.


*Note: You can name the template whatever you like, so long as you call the same name in the `middleman init` command*


##Adding a package with bower
By default, all bower packages are put in the ```components/``` directory outside of the source. This is to prevent all of the extra files bower downloads being copied over to ```build/```.
We used to have to symlink the files we wanted in the components directory over to our assets path in ```source/```, but no longer.

Now when you want to install a package, simply ```bower install <somepackage>``` and include it like you would any other file in sprockets.

If you want to reference the asset directly in your HTML, then you will need to create a file in the asset path that includes the asset via sprockets. It's not ideal, but I think thats the best I can do right now.  An example of this is ```source/assets/js/vendor/modernizr.js``` and ```source/assets/css/vendor/universal-ie6.css```.


##On the SCSS organization
I have not included a CSS grid at this time, mostly because it seems like everyone's got their own preference, and I haven't found one I really like yet.

However, I have included a file organization that has worked for me so far:
*any variables (like colors and such) go into _settings.scss
*any packages/imports go into _imports.scss

I'll likely be tweaking this a bunch as I go, however.


##Included helpers and other goodies
I have included a few helpers to help out with organizing information on your site. They are located in ```helpers/```.

To get typekit or analytics inclusion, simply add your account name/code to the appropriate places.

Also remember to add the site name, keywords, and description in ```helpers/meta. If you want to include a page-specific one of these, they will be appended to the overall site's.


##Contribute
Have a better idea for middleman defaults? Give it a fork! Don't hesitate to create an issue if you have a problem or question.

*Happy Building!*
