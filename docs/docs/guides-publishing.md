---
id: guides-publishing
title: Guide: Publishing
sidebar_label: Publishing
---

Noderize allows you to publish your module on npm with no additional step.

You simply have to build then publish to the registry:

```bash
yarn build
yarn publish
# or
npm run build
npm publish
```

If you want to preview what your package will look like instead, `build` then run `yarn pack` or `npm pack`. This will create a `.tgz` file which is identical to what is published.

## Automatically build

To automate building before publishing, you may want to add `scripts.prepublishOnly` to your `package.json` like so:

```json
"scripts": {
    "...": "...",
    "prepublishOnly": "noderize-scripts build --env production"
}
```

When using `yarn publish` or `npm publish`, it will first run build your package, then publish.

You may also want to run for tests before as well:

```json
"prepublishOnly": "noderize-scripts test --ci && noderize-scripts build --env production"
```