# feathers-react-iso-boilerplate

React Server Rendering
===
Dead simple rendering  with a custom router and a few components.
The conventional wisdom *seems* to be use a templating engine on top of
React, but `renderToStaticMarkup` is basically the same, so I use
it to render my document template.
<small>*(at least as of this writing, not sure when that was introduced)*</small>

Configuration
===
Routes config
`./src/routes.js`
Routes paths
`./src/components/pages`
An example of usage is already in each of those destinations.

Client Router
===
- Dead simple custom router on the client connects the client React
code to the already server rendered React elements.
- Added `./src/components/utils/Link.js`
<small>*Abstracts links and prevents their default behavior so that
when JS loads, the router can take over. These are to be used for
all internal links. Should be compatible with react-router as of
this writing.*</small>
- renamed all `<a />` tags to `<Link />` components.

Et voila! Server rendered isomorphic React application on Feathers.

Scripts
===
Added the following npm scripts

| script       | use |
|:-------------|:---:|
| start        | use nodemon to monitor dev server in `./src/server.js` |
| watchjs      | browserify client script with watchify <small>(continuous monitoring)</small>. entry point: `./src/lib/router.js` exports vendor scripts: `[ react , react-dom , mobx , mobx-react ]` |
| go           | run dev server without nodemon <small>(faster version for only working on client files)</small> and launches `watchjs` |
| minvendor    | bundle vendor scripts <small>(minified)</small> as separate from custom code bundle for better caching |
| build-server | transpile server code to node compatible js in `./dist` for more efficient node environment |
| minjs        | minifies custom code into a bundle <small>(excluding vendor code)</small>. endtry point: `./src/lib/router.js` |
| prod         | launch node server in `./dist/server.js` with env=production and store the PID in `pid.txt` |
| kill         | read PID from `./pid.txt` and end <small>(only used if running server with `prod`)</small> |


