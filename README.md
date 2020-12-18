This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app) and integrated the [NYCO Patterns library](https://nycopatterns.cityofnewyork.us) as a dependency **without ejection**. This integration is compatible with React Scripts **v3.4**. Version 4 of React Scripts introduces [breaking changes to asset include paths](https://github.com/facebook/create-react-app/issues/9870).

# React Scripts + NYCO Patterns integration

**$1** Install dependencies after [initializing a React Project](https://create-react-app.dev/docs/getting-started).

    npm install sass @nycopportunity/patterns @nycopportunity/patterns-framework@^0.2.4

* [**Dart Sass**](https://github.com/sass/dart-sass). This will enable [React Scripts'](https://github.com/facebook/create-react-app) use of the Webpack [sass-loader](https://webpack.js.org/loaders/sass-loader/) for compiling **.scss** files.

* [**NYCO Patterns library**](https://nycopatterns.cityofnewyork.us) (referred to as *library*).

* [**NYCO Patterns Framework**](https://github.com/CityOfNewYork/nyco-patterns-framework) (referred to as *framework*). The latest library is compatible with version `0.2.1` of the framework.

**$2** Use the `SASS_PATH` environment variable to configure your include paths. Initialize or add to your **.env** the following:

    SASS_PATH=src:node_modules/@nycopportunity:node_modules/@nycopportunity/patterns/src:node_modules/@nycopportunity/patterns-framework/src:node_modules/animate.scss

**$3** Change the **index.css** to **index.scss** and set the library's asset paths variables to use the local project's path.

    $cdn: '/src/';
    $path-to-fonts: 'fonts';
    $path-to-svg: 'svg';

**$4** Import patterns into the main stylesheet. The following line will import everything. [*View this repository's index.scss file to browse the import configuration options*](blob/main/src/index.scss).

    @import '~@nycopportunity/patterns/src/scss/imports';

**$5** Copy distributed assets from the NYCO Patterns framework into the src directory of the project:

    ./node_modules/@nycopportunity/patterns/dist/fonts > ./src/fonts
    ./node_modules/@nycopportunity/patterns/dist/svg > ./src/svg
    ./node_modules/@nycopportunity/patterns/dist/icons.svg > ./src/icons.svg

**$6** Run `npm start` to begin development.

---

**Notes**:

* The configuration above is largely dependent on what patterns in the library you will be using in your project. The above steps are based on the usage of *all* NYCO Patterns stylesheets.

* Node Sass can be used in place of Dart Sass, however, future pattern libraries will be migrating to Dart Sass.

* The latest version of the framework *may* be used but not all of the patterns in the library are be compatible with it.

* Below is a breakdown of the include paths for the `SASS_PATH` variable. Not all of them are required if only a few of the patterns are being used.

```
src
node_modules/@nycopportunity
node_modules/@nycopportunity/patterns/src
node_modules/@nycopportunity/patterns-framework/src
node_modules/animate.scss
```

* The font and svg assets only need to migrated into the project if using the NYCO Pattern's [fonts](https://github.com/IBM/plex) and/or [icons](https://nycopatterns.cityofnewyork.us/icons). You may also include fonts and svgs via [Google Fonts Embed](https://fonts.google.com/specimen/IBM+Plex+Sans) (fonts only) or the [CDN method of integration](https://github.com/CityOfNewYork/nyco-patterns-framework/blob/main/docs/installation.md#cdn).

* Icons still require the provided [Framework Utility Script](https://github.com/CityOfNewYork/nyco-patterns-framework/tree/main/src/utilities/icons) ([or a similar method](https://css-tricks.com/ajaxing-svg-sprite/)) to add them to the DOM. However, the CDN path to the distributed icons can be passed to the method as opposed to hosting them with the project.

* Guidance for this example is based on the following:
  * Create React App's [*Adding a Sass Stylesheet* documentation](https://create-react-app.dev/docs/adding-a-sass-stylesheet/)
  * Webpack's [*sass-loader* documentation](https://webpack.js.org/loaders/sass-loader/)

**Happy Coding!**

---

![The Mayor's Office for Economic Opportunity](NYCMOEO_SecondaryBlue256px.png)

[The Mayor's Office for Economic Opportunity](http://nyc.gov/opportunity) (NYC Opportunity) is committed to sharing open source software that we use in our products. Feel free to ask questions and share feedback. **Interested in contributing?** See our open positions on [buildwithnyc.github.io](http://buildwithnyc.github.io/). Follow our team on [Github](https://github.com/orgs/CityOfNewYork/teams/nycopportunity) (if you are part of the [@cityofnewyork](https://github.com/CityOfNewYork/) organization) or [browse our work on Github](https://github.com/search?q=nycopportunity).
