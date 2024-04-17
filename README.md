# /create with Cloudflare Workers

A [slash-create](https://npm.im/slash-create) template, using [Cloudflare Workers](https://workers.cloudflare.com).

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/Snazzah/slash-create-worker)

## Getting Started
### Cloning the repo
You can either use degit to locally clone this repo without git, or [create a new repo from this template](https://github.com/Snazzah/slash-create-worker/generate) and clone that.
```sh
npx degit Snazzah/slash-create-worker
```

After that, make sure to install dependencies using pnpm:
```sh
pnpm install
```
### Installing and setting up Wrangler
> Make sure to [sign up for a Cloudflare Workers account](https://dash.cloudflare.com/sign-up/workers) in a browser before continuing.
Install wrangler with npm or yarn:
```sh
volta install wrangler
# yarn global add wrangler@latest
```
Read more about [installing wrangler](https://developers.cloudflare.com/workers/cli-wrangler/install-update).

Afterwards, run `wrangler login` to login to your Cloudflare account with OAuth:
```sh
wrangler login
```

### Filling in secrets
You can enter in environment secrets with `wrangler secret put`, here are the keys that are required to run this:
```sh
npx wrangler secret put DISCORD_APP_ID
npx wrangler secret put DISCORD_PUBLIC_KEY
npx wrangler secret put DISCORD_BOT_TOKEN
```

### Development
To run this locally, copy `.env.example` to `.dev.vars` (used by `wrangler dev`) and fill in the variables, then you can run `pnpm run dev` to start a local dev environment and use something like ngrok to tunnel it to a URL.

To sync commands in the development environment, copy `.env.example` to `development.env` (used by `slash-up {command} -e development`) and fill in the variables, then run `pnpm run sync:dev`.

> Note: When you create a command, make sure to include it in the array of commands in `./src/commands/index.ts`.

### Production
To sync to production, copy `.env.example` to `.env` (used by `slash-up {command}`) and fill in the variables, then run `pnpm run sync`. To publish code to a worker, run `pnpm run deploy`.
