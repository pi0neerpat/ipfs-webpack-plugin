<h1 align="center">
  Example Gatsby app
</h1>

> This example demonstrates how to deploy a Gatsby.js site to IPFS using `ipfs-webpack-plugin`

This app was bootstrapped using the basic Gatsby starter template.

Create a new Gatsby app

```bash
gatsby new ./
```

Install `gatsby-plugin-ipfs` to the app by following these [instructions](https://github.com/moxystudio/gatsby-plugin-ipfs)

Add `ipfs-webpack-plugin` with

```bash
yarn add -D @zippie/ipfs-webpack-plugin
```

Update the Webpack config by adding the following to `gatsby-node.js`:

```js
const IPFSWebpackPlugin = require("@zippie/ipfs-webpack-plugin")

exports.onCreateWebpackConfig = ({ stage, loaders, actions }) => {
  if (stage === "build-html") {
    actions.setWebpackConfig({
      plugins: [new IPFSWebpackPlugin()],
    })
  }
}
```

Change the pinning address by updating `.env`

```
IPFS_BLOCK_PINNER_ADDRESS = http://localhost:5001
```

Start the IPFS node

```bash
docker-compose up
```

Build the Gatsby app

```bash
yarn build
```
