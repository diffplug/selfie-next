# selfie.dev

The landing page for [Selfie](https://github.com/diffplug/selfie-hackathon), distributed Storybook testing.

> Looking for the JVM/Python snapshot testing library (`expectSelfie`, `expect_selfie`)? It moved to [diffplug/selfie-lib](https://github.com/diffplug/selfie-lib), with docs at [lib.selfie.dev](https://lib.selfie.dev).

It's plain HTML and CSS in `public/`, with no build step, hosted on Cloudflare Pages.

```sh
pnpm install
pnpm dev     # serves public/ the way Pages does, including _redirects and 404.html
pnpm test    # checks the redirects, the links, and the 404 against that server
```

## Redirects

[`public/_redirects`](public/_redirects) comes from [selfie-hackathon#26](https://github.com/diffplug/selfie-hackathon/issues/26). Released jars and wheels link to these paths and can't be changed, so the redirects are permanent. **Don't reuse `/jvm`, `/py`, `/demo-gif`, `/go`, `/other-platforms`, or `/js` for anything on this site.**

## Deploying

`selfie.dev` is the custom domain of the `selfie-landing` Pages project. `lib.selfie.dev` stays on the separate `selfie` project.

Every push to `main` runs the tests, deploys `public/`, and runs the tests again against `https://selfie.dev` ([workflow](.github/workflows/site.yml)). Pull requests only run the tests. Deploying needs a `CLOUDFLARE_API_TOKEN` repository secret, with the Cloudflare Pages Edit permission.

To deploy by hand, run `pnpm run deploy`. It publishes your local `public/`, including anything uncommitted.

## Licenses

The logo and mascot come from [`branding/`](https://github.com/diffplug/selfie-hackathon/tree/main/branding) in selfie-hackathon, under Apache-2.0 ([LICENSE-branding](LICENSE-branding)). Jost is under OFL-1.1.
