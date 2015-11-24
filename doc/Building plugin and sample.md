## Building KendoUI Plugin and Sample

### Important Notes
- After running `jspm install` command remember to "fix" the `babelOptions` section of the generated `config.js` file to be:

```
babelOptions: {
    "optional": [
      "runtime",
      "optimisation.modules.system",
      "es7.decorators",
      "es7.classProperties"
    ]
  },

```
- After each change in `jspm`'s dependencies section of `package.json` file **make sure** that you run `jspm update` command (not `jspm install` command).


* * *

#### Step 1 
- Created empty repos initialized with README  **[plugin](https://github.com/adriatic-kendo/plugin)** and **[sample](https://github.com/adriatic-kendo/sample)**
- Created local clones in `C:\work\adriatic\ak\plugin` and `C:\work\adriatic\ak\sample`

***

#### Step 2 - Plugin creation
Dumped the content of the Aurelia Skeleton Plugin into `C:\work\adriatic\ak\plugin` folder and made the following modifications

##### Step 2.1
Updated the `package.json` jspm dependencies section to be
```
"jspm": {
    "main": "index",
    "format": "amd",
    "directories": {
      "lib": "dist/amd"
    },
    "dependencies": {
      "aurelia-binding": "npm:aurelia-binding@^1.0.0-beta.1.0.1",
      "aurelia-bootstrapper": "npm:aurelia-bootstrapper@^1.0.0-beta.1",
      "aurelia-dependency-injection": "npm:aurelia-dependency-injection@^1.0.0-beta.1",
      "aurelia-framework": "npm:aurelia-framework@^1.0.0-beta.1",
      "aurelia-http-client": "npm:aurelia-http-client@^1.0.0-beta.1",
      "aurelia-logging": "npm:aurelia-logging@^1.0.0-beta.1",
      "aurelia-metadata": "npm:aurelia-metadata@^1.0.0-beta.1",
      "aurelia-templating": "npm:aurelia-templating@^1.0.0-beta.1",
      "jquery": "github:components/jquery@^2.1.4",
      "kendo-ui": "github:telerik/kendo-ui-core@^2015.3.1111",
      "showdown": "github:showdownjs/showdown@1.3.0"
    },
```
(added the following three dependencies)
```
      "jquery": "github:components/jquery@^2.1.4",
      "kendo-ui": "github:telerik/kendo-ui-core@^2015.3.1111",
      "showdown": "github:showdownjs/showdown@1.3.0"
```
##### Step 2.2
Since the Kendo-UI-Core fetched from https://github.com/telerik/kendo-ui-core is now shipped with `.less` files (instead of `.css` files shipped previously), I added the file `kendo.common.min.css` to the folder `C:\work\adriatic\ak\plugin\jspm_packages\github\telerik\kendo-ui-core@2015.3.1111\styles\web` where all `.less` files live - so I do not have to deal with "less2css" compiler at this moment.

##### Step 2.3
In ordeer to be able to handle KendoUI PRO controls as well, I add the file `kendo.all.min.js` file to the folder `C:\work\adriatic\ak\plugin\jspm_packages\github\telerik\kendo-ui-core@2015.3.1111\src` where all other KendoUI-Core kendo plugins live.

##### Step 2.4
Added the complete content of the ["original plugin's" ](https://github.com/aurelia-ui-toolkits/aurelia-kendoui-plugin/tree/master/src) src folder

##### Step 2.5

Fixed the path to all kendo-ui--core plugins in all Aurelia "components" (`autocomplete.js`, `button.js`, `grid.js` and `tabstrip.js` from `import 'kendo-ui/src/js/` to `import 'kendo-ui/src/'`
* * *

#### Step 3 Sample creation

Dumped the content of the Aurelia Skeleton Plugin into `C:\work\adriatic\ak\sample` folder and made the following modifications

##### Step 3.1
Updated the `package.json` jspm dependencies section to be
```
  "jspm": {
    "dependencies": {
      "aurelia-animator-css": "npm:aurelia-animator-css@^1.0.0-beta.1",
      "aurelia-bootstrapper": "npm:aurelia-bootstrapper@^1.0.0-beta.1",
      "aurelia-fetch-client": "npm:aurelia-fetch-client@^1.0.0-beta.1",
      "aurelia-framework": "npm:aurelia-framework@^1.0.0-beta.1",
      "aurelia-history-browser": "npm:aurelia-history-browser@^1.0.0-beta.1",
      "aurelia-kendoui-plugin": "github:adriatic-kendo/plugin@master",
      "aurelia-loader-default": "npm:aurelia-loader-default@^1.0.0-beta.1.0.1",
      "aurelia-logging-console": "npm:aurelia-logging-console@^1.0.0-beta.1",
      "aurelia-router": "npm:aurelia-router@^1.0.0-beta.1",
      "aurelia-templating-binding": "npm:aurelia-templating-binding@^1.0.0-beta.1",
      "aurelia-templating-resources": "npm:aurelia-templating-resources@^1.0.0-beta.1.0.1",
      "aurelia-templating-router": "npm:aurelia-templating-router@^1.0.0-beta.1.0.1",
      "bootstrap": "github:twbs/bootstrap@^3.3.5",
      "fetch": "github:github/fetch@^0.10.1",
      "font-awesome": "npm:font-awesome@^4.4.0",
      "kendo-ui": "github:telerik/kendo-ui-core@^2015.3.1111",
      "showdown": "github:showdownjs/showdown@1.3.0",
      "systemjs/plugin-css": "github:systemjs/plugin-css@^0.1.17",
      "text": "github:systemjs/plugin-text@^0.0.3"
    },
```
##### Step 3.2
Since the Kendo-UI-Core fetched from https://github.com/telerik/kendo-ui-core is now shipped with `.less` files (instead of `.css` files shipped previously), I added the file `kendo.common.min.css` to the folder `C:\work\adriatic\ak\plugin\jspm_packages\github\telerik\kendo-ui-core@2015.3.1111\styles\web` where all `.less` files live - so I do not have to deal with "less2css" compiler at this moment.

##### Step 3.3
In order to be able to handle KendoUI PRO controls as well, I add the file `kendo.all.min.js` file to the folder `C:\work\adriatic\ak\sample\jspm_packages\github\telerik\kendo-ui-core@2015.3.1111\src` where all other KendoUI-Core kendo plugins live.

##### Step 3.4
Deleted the content of `C:\work\adriatic\ak\sample\src` folder and replaced it "wholesale" with the content of the original plugin's **[src](https://github.com/aurelia-ui-toolkits/aurelia-kendoui-plugin/tree/master/sample/src)** folder.

***Next steps are somewhat surprising, as I had to change the pathnames of the source files (when compared to original KendoUI plugin sample app***

##### Step 3.4
Changed the body of the **`index.html`** file to be
```
<body aurelia-app="src/main">
    <div class="splash">
      <div class="message">Aurelia Kendo Samples</div>
      <i class="fa fa-spinner fa-spin"></i>
    </div>

    <script src="jspm_packages/system.js"></script>
    <script src="config.js"></script>
    <script>
      System.import('aurelia-bootstrapper');
    </script>
   </body> 
```

##### Step 3.5
Changed the `main.js` file to be ***(note the need to add `src` prefix***)
```
import 'bootstrap';

export function configure(aurelia) {
    aurelia.use
        .standardConfiguration()
        .developmentLogging()

        .plugin('aurelia-kendoui-plugin', (kendo) => kendo.pro())

        .globalResources('src/shared/collapse-panel')
        .globalResources('src/shared/markdown');

    aurelia.start().then(a => a.setRoot('src/app'));
}
```

##### Step 3.6
Changed the `app.js` file to be ***(note the need to add `src` prefix***)
```
export class App {
    configureRouter(config, router) {
        config.title = 'Kendo UI Samples';
        config.map([{
            route: '',
            redirect: 'grid'
        }, {
            route: 'grid',
            moduleId: 'src/grid/index',
            nav: true,
            title: 'Grid'
        }, {
            route: 'button',
            moduleId: 'src/button/index',
            nav: true,
            title: 'Button'
        },  {
            route: 'comboboc',
            moduleId: 'src/combobox/index',
            nav: true,
            title: 'Combobox'
        },  {
            route: 'autocomplete',
            moduleId: '/src/autocomplete/index',
            nav: true,
            title: 'Autocomplete'
        }, {
            route: 'tabstrip',
            moduleId: 'src/tabstrip/index',
            nav: true,
            title: 'TabStrip'
        },]);

        this.router = router;
    }
}
```
