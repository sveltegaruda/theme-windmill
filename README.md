# svelte theme-windmill with routify

Theme for svelte (https://github.com/sveltegaruda/theme-windmill)

### Get started

To use a template, run

`npx degit sveltegaruda/theme-windmill my-project-name`

cd to my-project-name and then run

`pnpm i`
`npm run dev:nollup` or
`./x.cmd`

### npm scripts

| Syntax           | Description                                                                       |
|------------------|-----------------------------------------------------------------------------------|
| `dev`            | Development (port 5000)                                                           |
| `dev:nollup`     | Development with crazy fast rebuilds (port 5000)                                  |
| `dev-dynamic`    | Development with dynamic imports                                                  |
| `build`          | Build a bundled app with SSR + prerendering and dynamic imports                   |
| `serve`          | Run after a build to preview. Serves SPA on 5000 and SSR on 5005                  |
| `deploy:*`       | Deploy to netlify or now                                                          |
| `export`         | Create static pages from content in dist folder (used by `npm run build`)         |

### SSR and pre-rendering

SSR and pre-rendering are included in the default build process.

`npm run deploy:(now|netlify)` will deploy the app with SSR and prerendering included.

To render async data, call the `$ready()` helper whenever your data is ready.

If $ready() is present, rendering will be delayed till the function has been called.

Otherwise it will be rendered instantly.

See [src/pages/example/api/[showId].svelte](https://github.com/sveltech/routify-starter/blob/master/src/pages/example/api/%5BshowId%5D.svelte) for an example.

### Production

* For SPA or SSR apps please make sure that url rewrite is enabled on the server.
* For SPA redirect to `__dynamic.html`.
* For SSR redirect to the lambda function or express server.

### Issues?

File on Github! See https://github.com/sveltegaruda/theme-windmill/issues .