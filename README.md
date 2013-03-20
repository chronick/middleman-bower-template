#Headcanon's HTML5 Middleman + Bower template
This is a (somewhat opinionated) [Middleman](http://middlemanapp.com) template I made to help speed up static site building. It encourages asset management with [Bower](http://github.com/twitter/bower) and includes a default package.json. This template also makes it easy to add [Typekit](http://typekit.com) and [Google Analytics](http://google.com/analytics) to your site. 

a lot of credit goes to [Danny Prose's Middleman HTML5BP-HAML] template, as well as the general [HTML5 Boilerplate](http://html5boilerplate.com) for helping me make this template.

This bad boy is distributed under the MIT license.


##Features:
* [Markdown](http://daringfireball.net/projects/markdown/) rendering
* [SCSS](http://sass-lang.com)
* [Coffeescript](http://coffeescript.org)
* a [Favicon Maker](http://github.com/follmann/middleman-favicon-maker)
* Middleman [Live Reload](http://github.com/middleman/middleman-livereload)
* [Modernizr](http://modernizr.com)
* [Normalize.css](http://necolas.github.com/normalize.css) 
* [Universal IE6 CSS](http://github.com/malarkey/universal-ie6-css) for, well, IE6
* [Bower](http://github.com/twitter/bower) package management
* A Gemfile.ru for easy Heroku deployment
* A [middleman-deploy](http://github.com/tvaughan/middleman-deploy) config snippet to ease FTP deployment


##Installation
1. Download/clone to: `~/.middleman/html5bower`
2. Create your new Middleman project: `middleman init my_new_project --template=html5bower`
3. `bower install` to install the assets into a `components/` directory.

*Note: You can name the template whatever you like, so long as you call the same name in the `middleman init` command*


##Adding a package with bower
*This section just deals with adding bower packages to your middleman app.  The full bower documentation can be found [here](http://github.com/twitter/bower).*

I have included a few bower packages already in the component.json file, namely jquery, normalize, and modernizr, and have left the default components directory in the template's root. I did this because otherwise Middleman's build phase would copy *Everything* from each bower package into the build/ directory.

Also, middleman doesn't seem to support adding multiple asset paths at this time, so this is the easiest solution I could find for asset management without changing the source for [middleman-sprockets](http://github.com/middleman/middleman-sprockets).

In order to add a package, simply install the package with bower and symlink the files you want to use to the `source/assets/{css,js,img}/vendor` directory.

###Example
if I want to install jQuery, what I do is (from the project root):

    bower install jquery
    cd source/assets/js/vendor
    ln -s ../../../../components/jquery/jquery.min.js jquery.js

and include it wherever you like.

This tripped me up for a bit so I thought I'd say this:
If you wish to have a file concatenated into the main app.js or all.css, Sprockets requires you to prepend an underscore to the file, so it doesn't copy over the file *as well as* concatenate the contents.

If you do this for javascript, make sure to add the underscore again when you require the file, like so:

    //= require vendor/_jquery


##On the SCSS organization
I have not included a CSS grid at this time, mostly because it seems like everyone's got their own preference, and I haven't found one I really like yet.

However, I have included a file organization that has worked for me so far:
*any variables (like colors and such) go into _settings.scss
*any packages/imports go into _imports.scss

I'll likely be tweaking this a bunch as I go, however.


##Included helpers
I have included a few helpers to help out with orgainizing information on your site, as well as include typekit and google analytics easily. The helpers are found in config.rb.

To get typekit or analytics inclusion, simply add your account name/code to the appropriate places.

Also remember to add the site name, keywords, and description in config.rb. If you want to include a page-specific one of these, they will be appended to the overall site's.


##Contribute
Have a better idea for middleman defaults? Give it a fork! Don't hesitate to create an issue if you have a problem or question.

*Happy Building!*
