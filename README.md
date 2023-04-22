# QCObjects New App

This is a demo of a QCObjects based front-end Progressive Web App

# Open Live Demo

You can view the result of this project opening [QCObjects Demo App](https://newapp.qcobjects.dev) on any browser.

# Project Structure

The following is the project structure of a Progressive Web App made in QCObjects

```shell
.
├── css
│   ├── components
│   │   └── hero
│   ├── desktop
│   ├── mobile
│   └── theme
│       ├── basic
│       ├── cyan
│       ├── redlight
│       └── xtra
├── demo-tests
├── img
│   ├── icons
│   └── screenshots
├── js
│   └── packages
├── spec
│   └── support
└── templates
    └── components
        ├── hero
        └── pages

```

# Entry point

In index.html file, you will find this script:

```javascript
<script type="module" src="js/init.js"></script>
```

In the init.js file, you will find the main front-end settings:

```javascript
CONFIG.set("sourceType", "module");
CONFIG.set("relativeImportPath", "js/packages/");
CONFIG.set("componentsBasePath", "templates/components/");
CONFIG.set("delayForReady", 1); // delay to wait before executing the first ready event, it includes imports
CONFIG.set("preserveComponentBodyTag", false); // don't use <componentBody></componentBody> tag
CONFIG.set("useConfigService", false); // Load settings from config.json
CONFIG.set("routingWay","hash"); // routingWay possible values are 'hash','pathname','search'
CONFIG.set("useLocalSDK",true); // on the frontend side you can chose whether to load the SDK from sdk.qcobjects.dev or from your local website
CONFIG.set("tplextension","tpl.html"); // this is the file extension to locate the template files (if component.name = 'main' then template name will be main.tpl.html)
CONFIG.set("asynchronousImportsLoad",true); // it is recommended to load the Import declarations in an asyncronous way
CONFIG.set("serviceWorkerURI","/sw.js"); //QCObjects will register an launch this service worker automatically to work offline

```

You will also find the main imports:

```javascript
// note that this line is pure JavaScript ECMA2020
import "../QCObjects.js";
```

```javascript
Import("org.quickcorp.custom"); // this will load js/packages/org.quickcorp.custom.js file
```

Above Import function comes from QCObjects Framework
You can either use this function or import statement to load QCObjects packages.

# Enable QCObjects from local server

In package.json file, in scripts section, you will find some common commands that need to be present in every project that works with QCObjects.

# Run tests

The "test" script uses the "eslint" linter and the "jasmine" framework to check the code for errors and run tests. If any errors are found, the script tries to fix them automatically. If all tests pass, the script exits with code 0.

```shell
# Executes the tests of the project (see spec and coverage folders)
npm run test
```

# Run sync

The "sync" script stages and commits any changes made to the codebase. This is useful for keeping track of changes and making sure everything is up-to-date.

```shell
# Syncronizes the version between npm and git
npm run sync
```

# Run preversion

The "preversion" script runs "npm i --upgrade" and "npm test" before a new version of the package is published. This ensures that the latest version of the code is tested and ready to be released.

```shell
# This command is executed before a npm version is changed
npm run preversion
```

# Run postversion

The "postversion" script pushes the changes to the codebase and tags the new version. This helps keep track of the changes made to the code over time.

```shell
# This command is executed after a npm version is changed
npm run postversion
```

# Run coverage

The "coverage" script generates a code coverage report using the "nyc" library. This is useful for understanding how much of the code is being tested and where there may be gaps in test coverage.

```shell
# You can run this command to dispatch the coverage scripts (see coverage folder)
npm run coverage
```

# Run start

The "start" script runs the "createcert" and "serve" scripts. This is useful for quickly launching the app and getting started with development.

```shell
# Start the QCObjects Server
npm run start
```

The "serve" and "server" scripts launch the app using the "qcobjects" library. This is the main tool used in the development process.

```shell
# An alias to start the QCObjects Server
npm run serve
```

```shell
# An alias to start the QCObjects Server
npm run server
```

# Run QCObjects Collab

The "collab" script launches the collaborative coding tool "qcobjects-collab". This is useful for working with other developers on the same codebase.

```shell
# This command will open a shell with QCObjects Collab Tool
npm run collab
```

# Run QCObjects Shell

The "shell" script launches a shell terminal using the "qcobjects" library. This is useful for running commands and making changes to the codebase.


```shell
# This command will open a shell with QCObjects running
npm run shell
```

# Generate SSL certificates

The "createcert" script creates a certificate used for HTTPS connections. This is important for security reasons.
It uses letsencrypt certificate or openssl depending on settings. Default is openssl.

```shell
# This command will create a certificate for ssl
npm run createcert
```

# Dispatch a new version of your app

The "v-patch", "v-minor", and "v-major" scripts increment the version number of the package based on patch, minor or major changes. This is useful for keeping track of the changes made to the code over time.

```shell
npm run v-patch -m "message of commit" --git --npm
```

# Use the CLI with local dependencies

Install QCObjects CLI in local in order to use local dependencies and local settings of your project.

```shell
# This command will install QCObjects CLI in your local project
npm i --save-dev qcobjects-cli
```

The "qcobjects" script launches the "qcobjects" library command-line interface. This is the main tool used in the development process.

```shell
# This command will execute QCObjects CLI in your local project and show the version installed
npm run qcobjects -- --version
```

```shell
# To learn more about CLI commands, you can use the --help option
npm run qcobjects -- --help
```

```shell
# To learn more about CLI commands, you can use the --help option
npm run qcobjects -- create --help
```

# Launch a built-in HTTP Server 

The "http-server" script starts an HTTP server using the "qcobjects-cli" library. This is useful for testing the app in a local environment.

```shell
npm run http-server
```

# Publish your application to Google App Engine

The "gae-server" script starts a Google App Engine HTTP server using the "qcobjects-cli" library. This is useful for deploying the app to production.

Use this command in the settings of your GAE Application instead of "npm start"

```shell
npm run gae-server
```

# Build your application from TypeScript to JavaScript

The "build:ts" script compiles the TypeScript code and runs the linter to fix any issues. This is useful for ensuring that the code is properly formatted and free of errors.

The "build:ts-types" script generates TypeScript type declarations for the codebase. This is useful for making sure that the code is properly typed and free of errors.


```shell
# This command will be implemented in the future for TypeScript
npm run build
```

# Publish your application to test in local environment

The "publish:local" script publishes the package locally using the "qcobjects" library. This is useful for testing the app in a local environment.

# Prettify your code before commit to git

Finally, the "prepare" script installs the "husky" library, which is used to manage Git hooks. This is useful for automating tasks in the development process.

# Docker installation

To run this app with docker, execute the following command:

```shell
docker run -p 8080:8080 -p 8443:8443 --name qcobjects-newapp -d qcobjects/qcobjects-newapp
```

Then go to [https://127.0.0.1:8443/](https://127.0.0.1:8443/)
