# Walking Through Webpack

* Entry points
  - example: Angular main.ts

* Walk through dependency tree
  * Dependencies can be _anything_
    * JavaScript source code
      - (other modules)
    * Other language source code
      - (TypeScript, React, Vue, etc)
    * 3rd party modules
      - (e.g. installed by npm/yarn) 
    * Static Assets
      - (images, other files)
    * HTML Templates
      - (HTML, PUG, EJS, etc)

* Loaders
  * Compile/Transpile between languages
    - TypeScript to JavaScript
    - SCSS to CSS
    - ES2015+ to other variants
  * Discover other dependencies
    - Other modules (source code, libraries)
    - Other assets (e.g. HTML with `<img src="image1.jpg">` - `image1.jpg` is treated as a dependency, font files
    discovered from CSS/SCSS)
  * Add assets to the bundle
    - Files (images, fonts, html, etc)
    - Compiled CSS files
  * Inject additional code/modules
    - Polyfills
    
* Plugins
  * Provide more advanced functionality than loaders - access to everything about the build at every stage
    - Add new functionality, or override Webpack's default functionality
  * Use Webpack's hooks to integrate into different features of the compiler or stages of a compilation 
    * `HtmlWebpackPlugin` - Injects `<script>` and `<link>` tags into an HTML template for each of the generated bundle
    assets
    * `BundleAnalyzerPlugin` - Inspects the dependencies of a bundle and provides a treemap representation of the modules
    included
  * Can be complimentary to a loader - e.g. `AngularCompilerPlugin` and `@ngtools/webpack`, `VueLoaderPlugin` and `vue-loader`
    
Notes:
  * All app assets can (should!) be treated as dependencies, should not require a separate "copy" task

* What Now?
  * Code Splitting (demo)
    * Automatically split "vendor" code into its own chunk (instead of using explicit "vendors" entry point)
    * Split out code shared between entry points to improve caching/performance
    * Dynamic Imports - lazy load modules required for SPA routes
  * Tree Shaking (demo)
    * Possible with ES2015 module syntax (`import`/`export`)
    * Remove parts of source code that are not used

* WebpackDevServer (demo)
  * Watches bundle source for changes, automatically triggers recompilation
  * Automatically refreshes browser on completion
  * With HMR (Hot Module Replacement), can update CSS or even JS modules _without_ requiring browser refresh
