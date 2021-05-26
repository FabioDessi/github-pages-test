<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

        - [Team CHABLIS](#team-chablis)
- [oneAudi Feature App - Doc Renderer](#oneaudi-feature-app---doc-renderer)
  - [Description](#description)
    - [Content options](#content-options)
- [Getting Started](#getting-started)
      - [Links](#links)
  - [Notes](#notes)
  - [Prerequisites](#prerequisites)
    - [Environment variables](#environment-variables)
    - [Package access](#package-access)
  - [Project structure](#project-structure)
  - [Usage](#usage)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

##### Team CHABLIS

# oneAudi Feature App - Doc Renderer

## Description
Renders MD documentation files in React with Audi CI

### Content options
* Documentation File Url

# Getting Started
#### Links
[Demo (Latest)](https://oneaudi-feature-app-doc-renderer.cdn.dev.one.audi.com/next/index.html?spaceId=8l1afi0yxljy&environment=master&contentId=3Ne84WHpQMVoFyItIF0iWm&preview=true) \
[Test reports](https://fictional-happiness-72fe38e3.pages.github.io/) \
[Content](https://app.contentful.com/spaces/8l1afi0yxljy/entries/3Ne84WHpQMVoFyItIF0iWm) \
[Content Model](https://app.contentful.com/spaces/8l1afi0yxljy/content_types/oneAudiDocRenderer/fields) \
[Design](https://collaboration.msi.audi.com/confluence/display/OAOS/Documentation+Renderer+-+v1.0)

## Notes
* Use Node 14 &mdash; Earlier versions have known incompatibility issues, and later versions have not been tested.
* [React Testing Library](https://testing-library.com/docs/) is used for unit tests.
* Contentful &mdash; Learn about the [Contentful integration here](https://github.com/volkswagen-onehub/oneaudi-os/tree/832db977229e8b040911059aa164c42105cda07f/packages/contentful).
* Environment variables &mdash; Speak to someone in the team about their location. `process.env` [is not used in the frontend](https://github.com/webpack/changelog-v5/blob/master/MIGRATION%20GUIDE.md#user-content-level-5-runtime-errors); instead [DefinePlugin](https://webpack.js.org/plugins/define-plugin/) is used at compile time to make environment variables global constants. For production, they're set as [GitHub Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).
* Mock content is used in development environments. It's housed in `/mocks` and follows a similar structure to Contentful-provided data. You can switch to use published Contentful content by changing the expression in `FeatureApp.tsx`.

## Prerequisites
### Environment variables
Create a local `.env` file with the following variables:
- `CONTENTFUL_TOKEN`
- `CONTENTFUL_SPACE`
- `CONTENT_ID`

### Package access
NOTE: This needs to be completed only once for projects within this organisation. If you've already Enabled SSO for a project **that requires the same scopes as below**, skip this step.
1. [Create a Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) with the following scopes:
    * `repo:` Full
    * `write:packages`
2. Safely copy the token, and then **Enable SSO** for the `volkswagen-onehub` organisation. Return back to [the tokens page](https://github.com/settings/tokens) and click **Disable SSO** on the new token. A popover will appear - click **Enable SSO** again and authorise `audi`.
3. Locate your global `.npmrc` (or create if necessary) and add the following line with your pasted token appended:
    * `//npm.pkg.github.com/:_authToken=`
---

## Project structure
| Directory | Purpose |
| --------- | ------- |
| `.github/` | Base directory for GitHub actions (CI/CD) |
| `src/app/` | Base directory for the app |
| `src/assets/` | Images, icons, and other files used in the app |
| `mocks/` | Mock content |

## Usage
| Command | Purpose |
| ------- | ------- |
| `yarn` | Install dependencies. |
| `yarn serve` | Serve the application at http://localhost:3000. |
| `yarn format` | Format code with Prettier. |
| `yarn format:check` | Check format of code with Prettier. |
| `yarn lint` | Fix linting errors where possible. |
| `yarn lint:check` | Check for linting errors with ESLint. |
| `yarn test` | Execute Jest unit tests. |
| `yarn test:dev` | Execute Jest unit tests with watch. |
| `yarn test:e2e` | Execute Cypress tests. |
| `yarn test:e2e:open` | Start dev server and open Cypress. |
| `yarn lighthouse` | Run Lighthouse audit. |
