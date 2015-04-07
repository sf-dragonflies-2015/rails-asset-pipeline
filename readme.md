## Rails' Asset Pipeline

### Intro

* Assets are CSS, JS, image files
* Asset pipeline gives you precompilation, concatenation, and minification of assets in a centralized way
* The asset pipeline compiles Sass, CoffeeScript etc to CSS/JS
* (Sprockets gem)[https://github.com/sstephenson/sprockets] packages the assets for you
* It's all enabled by default and set up for you out of the box with Rails

### Asset organization in your app

* `app/assets` - First party assets that are specific to your app
* `lib/assets` - First party libraries that are written by your team or company that may be used across projects
* `vendor/assets` - Third party assets like javascript libraries or CSS frameworks
* `public/assets` - Where compiled assets are placed by the asset pipeline to be served as static assets in production

### Manifest files

* Manifest files tell the asset pipeline what files you want to require
* When a file is referenced in a manifest, sprockets will search for it in the three default asset locations

* `//=` syntax for reading directives
* Comments that are directives will be stripped out of the compiled files

* `require` directive --> inserts the contents of the asset source file specified
* `require_tree` directive --> recursively requires all files in all subdirectories of the directory specified
* `require_self` directive --> tells Sprockets to insert the body of the current source file before any subsequent directives


## Resources

(Asset Pipeline Rails Guide)[http://guides.rubyonrails.org/asset_pipeline.html]
(Sprockets)[https://github.com/sstephenson/sprockets]
