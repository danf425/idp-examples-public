# Boutique App Documentation

## Important Links

- [Workflow for creating docker image from any branch](https://app.harness.io/ng/#/account/vpCkHKsDSxK9_KYfjCTMKA/cd/orgs/default/projects/IDP_Settings_UI/pipelines/Docker_Image/pipeline-studio/)

### Getting Started

1. Install **NodeJS v16**. There are many ways to do this (**choose any one**):

   - Download relevant package from https://nodejs.org/download/release/v16.15.0/, unpack and install.
   - Use Homebrew: `brew install node@16`
   - If you already have Node installed, use `nvm` or `n` to install/select correct version. (see https://www.npmjs.com/package/n)

2. Install **yarn** package manager

```shell
$ brew install yarn
```

> Note: More options here: https://classic.yarnpkg.com/en/docs/install

3. Clone this repo

```shell
$ git clone https://github.com/harness/idp-settings-ui.git
$ cd idp-settings-ui
```

4. Add config to make Harness GitHub Package Registry accessible. Before running this step, make sure your GitHub personal access token is authorized for both "wings-software" and "harness", step is here: https://docs.github.com/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on

```shell
$ yarn setup-github-registry
```

5. Install/Update/Refresh dependencies

```shell
$ yarn
```

> Note: This will take some time the first time you run it. Subsequent runs should be near-instant. Run this everytime you change branches or take a pull. If there are no dependency changes, this is practically a no-op.

> Note: This is a shorthand for the command `yarn install`. Read more here: https://classic.yarnpkg.com/en/docs/usage

6. Compile/Build the code **and** start the web-server in watch mode

```shell
$ yarn dev
```

> Note: This will start the local server in watch mode with hot reloading. Any code changes will trigger fast patch rebuilds and refresh the page in the browser.

8. View in the browser

https://localhost:8185

### Integrating with NextGenUI

In [Harness Core UI](https://github.com/harness/harness-core-ui) (`develop` branch), run:

```sh
yarn setup-github-registry
touch .env
echo FF_IDP_ENABLED=true >> .env
echo ENABLE_IDP=true >> .env
echo TARGET_LOCALHOST=false >> .env

yarn
yarn dev
```

Access IDP Admin in Harness at https://localhost:8181
