### Project structure
```
<ProjectDir>
├── .env.development
├── .eslintignore
├── .eslintrc.js
├── .github
│   ├── workflows
├── .gitignore
├── .lighthouserc.json
├── .npmrc
├── .prettierignore
├── .prettierrc.js
├── cdk.json
├── CONTRIBUTING.md
├── cypress
│   ├── fixtures
│   ├── integration
│   ├── plugins
│   ├── support
│   ├── tsconfig.json
│   └── webpack.config.js
├── cypress.json
├── infrastructure
│   ├── environment.ts
│   ├── index.ts
│   ├── tsconfig.json
├── jest.config.js
├── oneaudi-cli.json
├── package.json
├── README.md
├── scripts
│   └── generate-serverless-config.js
├── server.js
├── src
│   ├── api
│   ├── app
│   ├── bootstrap.tsx
│   ├── index.html
│   ├── index.tsx
│   ├── integrator
│   └── test
├── tsconfig.json
├── webpack.config.js
└── yarn.lock
```

<img src="https://placeholder.com/150" />

![alt text](https://placeholder.com/150)


###### Team CHABLIS
# oneAudi Feature App - Stage
## Description
An immersive customer experience with full-screen videos and images.
### Content options
* Theme:
  * Light or Dark
* Image - Portrait (4:3)
* Image - Landscape (16:19)
* Video - Portrait (4:3)
* Video - Landscape (16:19)
* Video Config:
  * Autoplay
  * Loop
  * Display Native Controls
  * Muted
  * Allow Fullscreen
* Heading
* Heading Tag
* Subheading
* Primary and/or Secondary Button:
  * Label
  * Link
  * Open in new tab
* TextBox Position
* Show Shader
* WLTP:
   - Consumption data
   - Emission data
   - Disclaimer
* Show WLTP
* Media Content Disclaimer
# Getting Started
#### Resources
[Demo (Latest)](https://oneaudi-feature-app-stage.cdn.dev.one.audi.com/index.html?contentId=2iZ1dmn0Uj2Yl7GqIVpzKV) \
[Content](https://app.contentful.com/spaces/8l1afi0yxljy/entries/2iZ1dmn0Uj2Yl7GqIVpzKV) \
[Content Model](https://app.contentful.com/spaces/8l1afi0yxljy/content_types/oneaudiFeatureAppStage/fields) \
[Design](https://collaboration.msi.audi.com/confluence/pages/viewpage.action?pageId=259076969) \
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
3. Locate your global `.npmrc` (or create if necessary) and add the following lines, with your pasted token appending the second:
   * `//npm.pkg.github.com/:_authToken=`

---

## Project structure

| Directory         | Purpose                                   |
| ----------------- | ----------------------------------------- |
| `.github/`        | Base directory for GitHub actions (CI/CD) |
| `src/app/`        | Base directory for the app             |
| `src/assets/`        | Images, icons, and other files used in the app             |
| `mocks/`        | Mock content            |

## Usage

| Command                | Purpose                                                                                                                                             |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `yarn` | Install dependencies.
| `yarn serve` | Serve the application at http://localhost:3000. The Integrator demo will also be served at http://localhost:3000/demo.html.
| `yarn format` | Format code with Prettier.
| `yarn format:check` | Check format of code with Prettier.
| `yarn lint` | Fix linting errors where possible.
| `yarn lint:check` | Check for linting errors with ESLint.
| `yarn test` | Execute Jest unit tests.
| `yarn test:dev` | Execute Jest unit tests with watch.
| `yarn test:e2e` | Execute Cypress tests.
| `yarn test:e2e:open` | Start dev server and open Cypress.
| `yarn lighthouse` | Run Lighthouse audit.
