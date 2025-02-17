# B2B Mercury theme for VirtoCommerce Storefront

![image](https://user-images.githubusercontent.com/619699/147751949-c2a7e180-bf6c-4a68-a7b1-cbb6134f170f.png)

**B2B Mercury theme** is a fresh look on the field of eCommerce solutions. This is a place where common B2B and B2C scenarios are combined with the most bleeding edge technologies to deliver blazing fast and fully functional solution. It implements common business use-cases needed for a vast majority of projects we build.

This theme is designed to be used as-is within actual **VC Storefront**. You can modify it by implementing desired components, pages, shared logic to correspond with your project goals.

**VC Storefront Team** is proud to present **B2B Mercury theme** as a good starting point for new projects.

## Technologies used

- **Vue3.** Progressive frontend framework with its key features allows to build fast applications.
- **Typescript.** All components and composables have type definitions, so IDE can help you to build clean and working code.
- **TailwindCSS.** The most popular and growing CSS framework providing wonderful flexible structure to speed up styling.
- **Husky + ESLint + Prettier.** Autoformat, check and fix your code and prevent ugly codestyle within repository.
- **Vite.** It is faster than Webpack. Really FASTER. Use it to develop with HMR benefits and to build for production.
- **GraphQL.** Forget about REST, use flexible GraphQL queries and mutations to safely work with backend.

## Non-functional key features

- **Development performance.** Really fast development using the most effective solution. Enroll starter theme in seconds and start to modify code with HMR features.
- **Client performance.** We are supposed to reach and hold green metrics provided by Google PageSpeed Insights.
- **Decoupled structure.** Presentation layer is decoupled from backend. Shared logic is decoupled from visual components. Developer can concentrate on single task without the need of massive code manipulations.
- **Atomic Design Pattern.** Theme UI is based on Atoms, Molecules and Organisms, combined within Pages and shared Components. This provides a high level of code reusability.
- **Simple styling and theme customization.** We use TailwindCSS to provide the easiest and convinient way of CSS usage. Write as less of code as possible, reuse existing highly-customizable framework features.
- **Fully aligned with VirtoCommerce Storefront.** Thus theme is just a visual representation, we are fully aligned with VC Storefront to provide all common B2B and B2C scenarios processed by VC Platform.
- **Fully responsive.** We made our theme working on a number of devices from Desktops to Mobile phones, concentrated both on UI and UX.

## Theme structure

```text
├── assets                        // Images and other asset files used inside your application.
│   └── static
|       ├── bundle                // Scripts, styles and other assets compiled and minified for production.
|       ├── icons                 // Icons used for favicons, PWA, etc.
|       ├── images                // Static images used inside the application.
|       └── styles                // Common styles used inside the application.
├── client-app                    // The main folder for the application.
|   ├── components                // Atoms, Molecules, Organisms, used within whhole application.
|   |   └──....
|   ├── core                      // Common utilities and shared logic that can be used by any pages and libraries.
|   |   ├── api/graphql           // GraphQL Models aligned with the Virto Backoffice.
|   |   |   └──....
|   |   ├── composables           // Core composables (app-level shared logic).
|   |   |   └──....
|   |   ├── helpers               // Core helpers (functions, syntax sugar, etc).
|   |   |   └──....
|   |   ├── utilities             // Some miscellaneous utils.
|   |   |   └──....
|   |
|   ├── pages                     // Set of application pages used within Application router.
|   |   └──....
|   |
|   ├── shared                    // A set of shared files grouped by their domain context.
|   |   ├── catalog               // Grouping context (ex.: catalog browsing).
|   |   |   ├── components        // The collection of components specific for this domain context.
|   |   |   |   └──....
|   |   |   ├── composables       // The collection of shared logic written using Composable API pattern.
|   |   |   |   └──....
|   |   |   ├── types             // Types used in this context.
|   |   |   |   └──....
|   |   |   └── index.ts          // Entry point for this context used as library.
|   |   |
|   |   └──....
|   |
|   ├── App.vue                   // Main Application component. Use it as a wrapper for routable pages.
|   ├── env.d.ts                  // Definition file to provide IDE IntelliSense support for importing *.vue files.
|   ├── main.ts                   // Application entry point. Main initialization script.
|   ├── router.ts                 // SPA routing configuraion.
|   └── shims-graphql.d.ts        // Definition file to provide IDE IntelliSense support for importing *.graphql files.
|
├── config                        // The Virto theme settings.
|   └── settings_data.json        // The json file contains all the main settings for the theme.
|
├── layout                        // Layout templates used to render theme within Storefront.
|   └──theme.liquid               // Wrapper for SPA, providing HTML document structure.
|
├── locales                       // Locale files used to provide translated content for the theme.
|   └──....
|
├── templates                     // Liquid templates, used in SSR and MPA. Each MPA page needs to have a liquid template here if you want SSR.
|   └──index.liquid               // Entry point for SPA, providing container with necessary scripts and styles.
|
├── .browserslistrc               // Browserslist config file to support actual versions of browsers.
├── .commitlintrc.json            // Config for Conventional commit hook.
├── .editorconfig                 // Common editor settings to sync codestyle.
├── .env                          // Envfile to define different Environment Variables.
├── .eslintignore                 // Ignore some files from ESlint.
├── .eslintrc                     // ESlint configuration file.
├── .gitignore                    // Ignore some files from GIT.
├── .prettierignore               // Ignore some files from Prettier.
├── .prettierrc                   // Config for Prettier.
├── README.md                     // This file.
├── graphql.codegen.yml           // GraphQL configuration file to generate types for schemas from your Virto Backoffice url.
├── gulpfile.js                   // Artifact build script to product zip-file installable by VC Storefront.
├── index.html                    // Vite Development entry point.
├── package.json                  // NPM Package description.
├── postcss.config.js             // PostCSS configuration for Tailwind.
├── tailwind.config.js            // TailwindCSS configuration file.
├── tsconfig.json                 // TypeScript configuration file.
├── vite.config.ts                // Vite configuration file.
```

## Getting started

### Prerequisites

- Install `vc-platform` 3.x the latest version. [Deploy on Windows](https://github.com/VirtoCommerce/vc-platform/blob/master/docs/getting-started/deploy-from-precompiled-binaries-windows.md) or [Deploy on Linux](https://github.com/VirtoCommerce/vc-platform/blob/master/docs/getting-started/deploy-from-precompiled-binaries-linux.md)
- Install `vc-module-experience-api` module. [Getting started](https://github.com/VirtoCommerce/vc-module-experience-api/blob/dev/docs/getting-started.md)

### Install the `vc-storefront`

- Clone [https://github.com/VirtoCommerce/vc-storefront](https://github.com/VirtoCommerce/vc-storefront) in to a local folder

- Open the **appsettings.json** file in a text editor.
- In the **Endpoint** section change **Url**, **UserName**, **Password** with correct path and credentials for Virto Commerce Platform:

```json
...
 "Endpoint": {
     "Url": "https://localhost:5001",
     "UserName": "admin",
     "Password": "store",
```

### Setup `B2B Mercury theme`

```bash
# Clone repo into the folder where storefront is installed
git clone https://github.com/VirtoCommerce/vue-starter-theme.git "C:\vc-storefront\wwwroot\cms-content\themes\{store-name}\default"
# Change the current directory
cd C:\vc-storefront\wwwroot\cms-content\themes\{store-name}\default
# install dependencies
yarn
# Start theme in development mode with HMR support
yarn dev
# or build theme to get installable artifact
yarn compress
```

### Run `vc-storefront` application

```bash
# change the current directory
cd C:\vc-storefront
# build and run storefront application
dotnet run
```

## License

Copyright (c) Virtosoftware Ltd. All rights reserved.

Licensed under the Virto Commerce Open Software License (the "License"); you
may not use this file except in compliance with the License. You may
obtain a copy of the License at

[https://virtocommerce.com/opensourcelicense](https://virtocommerce.com/opensourcelicense)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied.
