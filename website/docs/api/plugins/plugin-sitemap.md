---
sidebar_position: 10
slug: /api/plugins/@docusaurus/plugin-sitemap
---

# 📦 plugin-sitemap

import APITable from '@site/src/components/APITable';

This plugin creates sitemaps for your site so that search engine crawlers can crawl your site more accurately.

:::caution production only

This plugin is always inactive in development and **only active in production** because it works on the build output.

:::

## Installation {#installation}

```bash npm2yarn
npm install --save @docusaurus/plugin-sitemap
```

:::tip

If you use the preset `@docusaurus/preset-classic`, you don't need to install this plugin as a dependency.

You can configure this plugin through the [preset options](#ex-config-preset).

:::

## Configuration {#configuration}

Accepted fields:

<APITable>

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `changefreq` | `string` | `'weekly'` | See [sitemap docs](https://www.sitemaps.org/protocol.html#xmlTagDefinitions) |
| `priority` | `number` | `0.5` | See [sitemap docs](https://www.sitemaps.org/protocol.html#xmlTagDefinitions) |
| `ignorePatterns` | `string[]` | `[]` | A list of glob patterns; matching route paths will be filtered from the sitemap. Note that you may need to include the base URL in here. |
| `filename` | `string` | `sitemap.xml` | The path to the created sitemap file, relative to the output directory. Useful if you have two plugin instances outputting two files. |

</APITable>

:::info

This plugin also respects some site config:

- [`noIndex`](../docusaurus.config.js.md#noIndex): results in no sitemap generated
- [`trailingSlash`](../docusaurus.config.js.md#trailingSlash): determines if the URLs in the sitemap have trailing slashes

:::

### Example configuration {#ex-config}

You can configure this plugin through preset options or plugin options.

:::tip

Most Docusaurus users configure this plugin through the preset options.

:::

```js config-tabs
// Preset Options: sitemap
// Plugin Options: @docusaurus/plugin-sitemap

const config = {
  changefreq: 'weekly',
  priority: 0.5,
  ignorePatterns: ['/tags/**'],
  filename: 'sitemap.xml',
};
```

You can find your sitemap at `/sitemap.xml`.
