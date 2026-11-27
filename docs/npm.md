# Publish `@publishpress/potomatic` on npmjs.com

This package is scoped as **`@publishpress/potomatic`**. It is not the unrelated [`potomatic`](https://www.npmjs.com/package/potomatic) package on npmjs.com.

## Org and team (`developers`)

1. An npm user with **owner** access to the **`publishpress`** org signs in at [npmjs.com](https://www.npmjs.com/).
2. Under **Organizations → publishpress → Teams**, ensure the **`developers`** team exists.
3. After the first publish, grant the team publish access:

```bash
npm access grant read-write developers:publishpress @publishpress/potomatic
```

Add `developers` members under **Teams → developers → Members**.

## Automation token (GitHub Actions)

1. **Access Tokens → Generate New Token** (granular).
2. Packages: **Read and write**, scope packages under `@publishpress` (or this package once it exists).
3. In GitHub **`publishpress/library-potomatic`** → **Secrets and variables → Actions**, create **`NPM_PUBLISH_TOKEN`**.

## First publish

Publish a GitHub **Release** whose tag is `v` plus the `version` in `package.json` (for example `v1.4.3`). The **Publish npm** workflow publishes to npmjs.com.

Local smoke test (optional):

```bash
npm ci && npm test && npm publish --access public
```

## Consumers

```bash
npm install @publishpress/potomatic
```
