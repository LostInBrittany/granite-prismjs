[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/LostInBrittany/granite-prismjs)

## granite-prismjs

*granite-prismjs* is a wrapping of [Prism.js](http://prismjs.com/) CSS as [Polymer](https://www.polymer-project.org/) [shared styles modules](https://www.polymer-project.org/1.0/docs/devguide/styling.html#style-modules) (i.e. inside `<dom-module>` tags).

> Hybrid Polymer element, 1.x-2.x ready

## Doc & demo

[https://lostinbrittany.github.io/granite-prismjs](https://lostinbrittany.github.io/granite-prismjs)



### Using *granite-prismjs* modules

Using  polymer [shared styles](https://www.polymer-project.org/1.0/docs/devguide/styling.html#style-modules) modules is a two-step process: you need to use a `<link>` tag to import the module, and a `<style>` tag to include the styles in the correct place.

To use *granite-prismjs* in an element:

#### 1. Add the dependency

Add the dependency to the `bower.json` of your application:

```
   "dependencies": {
     [...]
     "granite-prismjs": "LostInBrittany/granite-prismjs#^1.8.3"
   }
``` 

And then recover them via `bower install`.


#### 2. Import the *granite-prismjs* module you want to use

Usually you will simply want to import `granite-prismjs.html` (wrap around `prismjs.css`) or any other of the prism themes, each one in  it's own HTML file as a style module..

Supossing you're using the standard folder locations for your components:
 
```
<link rel="import" href="../granite-prismjs/granite-prismjs.html">
``` 

#### 3. Inside your component, use *granite-prismjs* as shared style

In your element's template you add the include for the *granite-prismjs* module:

```
<style include="granite-prismjs"></style>
```
 

#### A complete example

```
<!-- import the module  -->
<link rel="import" href="../granite-prismjs/granite-prismjs.html">
<dom-module id="x-foo">
  <template>
    <!-- include the style module by name -->
    <style include="granite-prismjs"></style>
    <style>:host { display: block; }</style>
    Hi
  </template>
  <script>Polymer({is: 'x-foo'});</script>
</dom-module>
```
 


### Generating the style modules

To generate the style modules we use the [granite-css-modularizer](https://github.com/LostInBrittany/granite-css-modularizer) node script:

#### 1. Clone the repository and recover the dependencies of `granite-css-modularizer`

Clone the [granite-css-modularizer](https://github.com/LostInBrittany/granite-css-modularizer) repository and recover the dependencies using `yarn` (or `npm`) :

```
$ yarn install
yarn install v1.2.1
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
Done in 0.83s.
```

#### 2. Recover Prism.js 

Recover Prism.js themesribution using `yarn` (or `npm`):

```
$ yarn add prismjs@1.8.3
yarn add v1.2.1
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
└─ prismjs@4.0.01.8.3
Done in 0.55s.
```

Currently *granite-prismjs* uses Prism.js version 1.8.3, if you need another version you can change simply install it.


#### 3. Generate the components

Using NodeJS and the `granite-css-modularizer.js` to transform Prism.js CSS files into polymer elements.

```
$ node ../granite-css-modularizer.js ./node_modules/prismjs/themes/css ./css_modules/granite-prismjs
```

After executing it, a series of HTML files is generated in the `./css_modules/granite-prismjs` folder, each one corresponding to a Prism.js CSS file.

```
$ ls ./css_modules/granite-prismjs/*.html
granite-prism-coy.html   granite-prism-funky.html  granite-prism-okaidia.html         granite-prism-tomorrow.html
granite-prism-dark.html  granite-prism.html        granite-prism-solarizedlight.html  granite-prism-twilight.html```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Note on semver versioning

I'm aligning the versions of this element with Prism.js version, in order to make easier to choose the right version
 
## License

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
