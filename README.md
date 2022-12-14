# promo-button-node, by [Tincre`.dev`](https://tincre.dev/promo)

Node and other utilities for the [`promo-button`](https://github.com/Tincre/promo-button). 

## Installation

Use your favorite package manager to rock installation of `promo-button-node`.

### Yarn
```
yarn add @tincre/promo-button-node # -D if you want this as a dev dep
```
### Npm

```
npm install @tincre/promo-button-node # --save-dev if you want it as a dev dep
```

### Environment variables 

You'll need the following environment variables available in Node.js:

- `PROMO_CLIENT_ID`
- `PROMO_CLIENT_SECRET` 
- `PROMO_APP_ID`
- `PROMO_API_KEY` (optional)

These values can be found in the [Tincre.dev Dashboard](https://tincre.dev/dashboard)
after you're logged in and have created at least one app. 

#### `.env.local` Example

```env 
PROMO_API_KEY=
PROMO_CLIENT_ID=
PROMO_APP_ID=
PROMO_CLIENT_SECRET=
```
### Usage 

#### `generateAccessToken`

```js
/* An example to hit the promo-api /campaigns endpoint */
import { generateAccessToken } from '@tincre/promo-button-node';

const formData = {...}; // campaign submission data, see https://tincre.dev/docs
const clientSecret = process.env.PROMO_CLIENT_SECRET || "";
const appId = process.env.PROMO_APP_ID || "";
const clientId = process.env.PROMO_CLIENT_ID || "";
let accessTokenSigned = generateAccessToken(
  "http://localhost:3000", // update w/hostname + base route
  clientId,
  appId,
  clientSecret
);
let resultToken = await getToken(accessTokenSigned);
const headers = {
  "Content-Type": "application/json",
  Authorization: `Bearer ${resultToken}`,
};

const promoApiRes = await fetch(`https://promo.api.tincre.dev/campaigns`, {
  method: "POST",
  headers: headers,
  body: JSON.stringify(formData),
});
```

## Support 

- Documentation: [tincre.dev/docs](https://tincre.dev/docs)
- Guides and how-tos: [tincre.dev/docs/guides](https://tincre.dev/docs/guides) 
- Reference docs: [tincre.dev/docs/reference](https://tincre.dev/docs/reference)
- Community: [community.tincre.dev](https://community.tincre.dev)

## License 

This code is free to use for your commercial or personal projects. It is open-source 
licensed under the [Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/2.0/).

You will see various headers throughout the codebase and can reference the license 
directly via [LICENSE](/LICENSE) herein.

## Development 

### Releases 

We use [`npm`](https://npmjs.com) for releases. In particular, we use
`npm --publish` to get the job done.

Currently, only @thinkjrs has the ability to release. The following section 
is written for memory.

#### Release prep

Prior to using `npm --publish` a release tag needs to be created for
the library using our standard tagging practices. 

> Ensure that tests :white_check_mark: pass during this process prior to
releasing via npm.

##### Test release 

To do a proper release, ensure you're in the base repo directory and run 
`npm publish . --access public --dry-run`.

#### Release `latest` tag

To complete a full release to the `latest` npm `dist-tag`, ensure you're in
the base repo directory and run `npm publish . --access public`. 

:tada: That's it! :tada:
