# Project Setup 

## Install Dependencies
Install docsify-cli and nodemon as devDependencies

```bash
npm i docsify-cli nodemon -D --only=dev
```

Add the following script in package.json
```json
    "docsify": "docsify",
    "serve": "docsify serve docs --port 8888",
    "watch": "nodemon"
```
Initialize docsify in docs directory.
```bash
npm run docsify -- init ./docs
```

Add nodemon.json
```json
{
    "verbose": true,
    "ext": "js,json,html,md",
    "watch": [
        "docs/*"
    ],
    "ignore": [
        ".git",
        "node_modules/**/node_modules"
    ],
    "exec": "npm run serve"
}
```

Start the local server with nodemon.
```bash
npm run watch
```

## Configure Theme
Use docsify-themeable Simple Theme for example.

Remove or comment out the original css.
```html
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
```

Add the theme css
```html
  <!-- Theme: Simple (latest v0.x.x) -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple.css">
```

Add the theme js
```html
  <!-- docsify-themeable (latest v0.x.x) -->
  <script src="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/js/docsify-themeable.min.js"></script>
```

## Plugin List
- [Docsify Plugins List](https://docsify.js.org/#/plugins)
- [awesome-docsify](https://docsify.js.org/#/awesome?id=plugins)
```html
  <script src="//unpkg.com/docsify-variables/dist/docsify-variables.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/@alertbox/docsify-footer/dist/docsify-footer.min.js"></script>
  <script src="//unpkg.com/docsify/lib/plugins/ga.min.js"></script>
  <!-- docsify-tabs (latest v1.x.x) -->
  <script src="https://cdn.jsdelivr.net/npm/docsify-tabs@1"></script>
  <!-- 
    docsify uses Prism to highlight code blocks in your pages. 
    By default it only supports CSS, JavaScript and HTML. 
    You can make Prism load additional languages.
    Check the component files list for more options:
    https://github.com/PrismJS/prism/tree/gh-pages/components
  -->
  <script src="//unpkg.com/prismjs/components/prism-bash.min.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-php.min.js"></script>
```

## Configuration
The complete configuration is at [Docsify Configuration](https://docsify.js.org/#/configuration)
```js
    window.$docsify = {
      name: 'Taylor\'s Notes',
      nameLink: '/',
      repo: 'https://github.com/cytaylorw/docsify-tech-notes',
      coverpage: false,
      loadSidebar: true,
      subMaxLevel: 2,
      loadNavbar: true,
      loadFooter: true,
      auto2top: true,
      themeable: {
          // readyTransition : true, // default
          // responsiveTables: true  // default
      },
      variablesFile : 'variables.json',
      variablesFileType : 'json',
      ga: 'UA-XXXXX-Y'
    }
```