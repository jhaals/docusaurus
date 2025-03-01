---
sidebar_position: 5
slug: /api/plugins/@docusaurus/plugin-debug
---

# 📦 plugin-debug

```mdx-code-block
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
```

The debug plugin will display useful debug information at [http://localhost:3000/\_\_docusaurus/debug](http://localhost:3000/__docusaurus/debug).

It is mostly useful for plugin authors, that will be able to inspect more easily the content of the `.docusaurus` folder (like the creates routes), but also be able to inspect data structures that are never written to disk, like the plugin data loaded through the `contentLoaded` lifecycle.

:::info

If you use the plugin via the classic preset, the preset will **enable the plugin in development and disable it in production** by default (`debug: undefined`) to avoid exposing potentially sensitive information. You can use `debug: true` to always enable it or `debug: false` to always disable it.

If you use a standalone plugin, you may need to achieve the same effect by checking the environment:

```js title="docusaurus.config.js"
module.exports = {
  plugins: [
    // highlight-next-line
    process.env.NODE_ENV === 'production' && '@docusaurus/plugin-debug',
  ].filter(Boolean),
};
```

:::

:::note

If you report a bug, we will probably ask you to have this plugin turned on in the production, so that we can inspect your deployment config more easily.

If you don't have any sensitive information, you can keep it on in production [like we do](/__docusaurus/debug).

:::

## Installation {#installation}

```bash npm2yarn
npm install --save @docusaurus/plugin-debug
```

:::tip

If you use the preset `@docusaurus/preset-classic`, you don't need to install this plugin as a dependency.

You can configure this plugin through the preset options.

:::

## Configuration {#configuration}

This plugin currently has no options.

### Example configuration {#ex-config}

You can configure this plugin through preset options or plugin options.

:::tip

Most Docusaurus users configure this plugin through the preset options.

:::

<Tabs>
<TabItem value="Preset Options">

If you use a preset, configure this plugin through the [preset options](../../using-plugins.md#docusauruspreset-classic):

```js title="docusaurus.config.js"
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        // highlight-next-line
        debug: true, // This will enable the plugin in production
      },
    ],
  ],
};
```

</TabItem>
<TabItem value="Plugin Options">

If you are using a standalone plugin, provide options directly to the plugin:

```js title="docusaurus.config.js"
module.exports = {
  // highlight-next-line
  plugins: ['@docusaurus/plugin-debug'],
};
```

</TabItem>
</Tabs>
