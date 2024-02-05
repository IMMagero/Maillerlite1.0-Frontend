# Project Description

A simple project for listing and adding a subscriber

## Project Development and Test Environment
Below are the infrastructure requirements that the project has been built and tested on:

OS - Windows 10
Package Manager - NPM v10.2.4
Browser - Chrome v121.0.6167.140


## 💿 Install

Set up your project using your preferred package manager. Use the corresponding command to install the dependencies:

| Package Manager                                                | Command        |
|---------------------------------------------------------------|----------------|
| [yarn](https://yarnpkg.com/getting-started)                   | `yarn install` |
| [npm](https://docs.npmjs.com/cli/v7/commands/npm-install)     | `npm install`  |
| [pnpm](https://pnpm.io/installation)                          | `pnpm install` |
| [bun](https://bun.sh/#getting-started)                        | `bun install`  |

After completing the installation, your environment is ready for development.

## 💡 Usage

This section covers how to start the development server and build your project for production and the change if necessary for the API integration.

### How to configure the API that has been integrated with the App

- Navigate to vite.config.js
- Change only the target URL of both the proxies to match where you have deployed your API (The lines that need to be changed are 48 and 65 respectively)

### Starting the Development Server

To start the development server with hot-reload, run the following command. The server will be accessible at [http://localhost:3000](http://localhost:3000):

```bash
npm run dev
```

(Repeat for yarn, pnpm, and bun with respective commands.)

> NODE_OPTIONS='--no-warnings' is added to suppress the JSON import warnings that happen as part of the Vuetify import mapping. If you are on Node [v21.3.0](https://nodejs.org/en/blog/release/v21.3.0) or higher, you can change this to NODE_OPTIONS='--disable-warning=5401'. If you don't mind the warning, you can remove this from your package.json dev script.

### Building for Production

To build your project for production, use:

```bash
npm run build
```

(Repeat for yarn, pnpm, and bun with respective commands.)

By default, the build output will be placed at dist. You may deploy this dist folder to any of your preferred platforms.

Once the build process is completed, your application will be ready for deployment in a production environment.

To preview the project run:
```bash
npm run preview
```

The project will preview and accessed via:

http://localhost:4173/

## 📑 License
[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2016-present Vuetify, LLC
