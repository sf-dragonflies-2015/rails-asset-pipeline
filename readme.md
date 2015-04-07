## Rails' Asset Pipeline

### Intro

* Assets are CSS, JS, image files
* Asset pipeline gives you precompilation, concatenation, minification, and fingerprinting of assets in a centralized way
* The asset pipeline compiles Sass, CoffeeScript etc to CSS/JS
* [Sprockets gem](https://github.com/sstephenson/sprockets) packages the assets for you
* It's all enabled by default and set up for you out of the box with Rails

### Asset organization in your app

* `app/assets` - First party assets that are specific to your app
* `lib/assets` - First party libraries that are written by your team or company that may be used across projects
* `vendor/assets` - Third party assets like javascript libraries or CSS frameworks
* You don't need to do anything in the layout to get assets included
* Assets are placed here by the asset pipeline to be served as static assets in production: `public/assets`


### Manifest files

* Manifest files tell the asset pipeline what files you want to require
* When a file is referenced in a manifest, sprockets will search for it in the three default asset locations
* `//=` (JS) or `*=` (CSS) syntax for reading directives
* Comments that are directives will be stripped out of the compiled files
* By convention each controller has an associated css and a js manifest file (if you use a generator, that's created for you)
* For example: `app/assets/javascripts/posts.js` and `app/assets/stylesheets/posts.css` if you have a `PostsController`

#### Common directives
* `require` inserts the contents of the asset source file specified
* `require_tree` recursively requires all files in all subdirectories of the directory specified
* `require_self` insert the body of the current source file at the location of this line

### Index files

* The asset pipeline will treat files named `index` as a manifest for the directory its in
* This helps with organizing sub-groups of assets

### Asset location helpers

* You have some helpers available to you to find the location of asset files
* `asset_path` to get the path of an image, for example:
  `.class { background-image: url(<%= asset_path 'image.png' %>) }`
* `asset_uri` to get the uri
* If you put a `.erb` extension on your css files, the asset pipeline will automatically evaluate that erb

### Helpful rake tasks

* `rake assets:precompile`
* `rake assets:clean`
* `rake assets:clobber`

## Resources

[Asset Pipeline Rails Guide](http://guides.rubyonrails.org/asset_pipeline.html)
[Sprockets](https://github.com/sstephenson/sprockets)
