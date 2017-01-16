# Cordova Template for Phaser, using Typescript and Jed
A Cordova/PhoneGap template for building a Phaser game using Typescript.  Both [Jed](https://slexaxton.github.io/Jed/) and [po2json](https://github.com/mikeedwards/po2json) have been included to assist in any internationalization (i18n) efforts.

The workflow provided by this template will assume control of the `www` directory.  Any content added or changed in this directory manually will be overridden or removed by the provided Grunt tasks.

Features include:
* [Phaser](http://phaser.io/) 
* [Grunt](http://gruntjs.com/) - New to Grunt? Check out [http://gruntjs.com/getting-started](http://gruntjs.com/getting-started) to see how to set it up.
  * [Express](https://github.com/blai/grunt-express) - Provides a Grunt-based server used in tandem with `grunt-contrib-watch` to provide live-reloading when debugging.
* [Typescript](https://www.typescriptlang.org/)
  * [TSLint](https://palantir.github.io/tslint/) - Verify TypeScript against Phaser's recommended code styles.
  * [Typings](https://www.npmjs.com/package/typings) - Provides typing information for TypeScript development.
  * [webpack](https://webpack.js.org/) - Combines source code and typings to compile TypeScript into a single JavaScript package.
* [Jed](https://slexaxton.github.io/Jed/)
  * [po2json](https://github.com/mikeedwards/po2json) - Convert your translation files into JSON that can be used by Jed.

## Quickstart
To use this template with `cordova`, create a new Cordova project with the `--template` parameter.

```
cordova create <directory> <project-scope> <project-name> --template cordova-phaser-ts-jed 
```

NOTE: `<project-scope>` should resemble `com.example.<directory>`, although the decision is ultimately yours.

Once the project has been created, run the following:

```
npm install
```

After installation, all packages should be ready to use in the `<directory>` indicated.  You should update the generic `package.json` and `src/html/index.html` files to with the name and version of the project, as applicable.

To initially populate the `www` directory, or update the `www` directory with any changes, use the following command:

```
grunt build
```

Top start a server for the project, use the command:

```
grunt serve
```

This will start a server at [http://localhost:9000](http://localhost:9000) on your computer.  You can open this page in your default browser by changing the command to `grunt open serve`.

While being served, you can use `F5` (or `<cmd>-R`) to reload the page in the browser.  Use `<ctrl>-C` on the command line to stop the server.

Or, if you plan to actively develop your project and need live reload, use the command:

```
grunt debug
```

This will copy any asset or static file changes immediately, as well as recompile any changed TypeScript files.  The task will automatically reload the page opened in your browser once the changes propagate into the `www` directory.

The page served by this task can also be manually reloaded in the browser, or aborted on the command line.

If you only want to update code changes without a server, you can use the command:

```
grunt watch
```

## Project Structure
This template organizes content with the following structure:

- **assets** - Used to store all of your project's assets.  All content will be copied into `www/assets` when the project is built.
- **src** - All source files related to your project.
  - **html** - All files and directories here are copied into `www` without any processing.
    - **index.html** - A default HTML file.
  - **translations** - Store all `.po` files in this directory.
  - **ts** - All TypeScript files should be placed in this directory.
    - **states** - A sample directory of Phaser states.
      - **boot.ts** - A sample Phaser state that is called when the app is started.
      - **preload.ts** - A sample Phaser state that is called directly after the boot state is completed.
      - **states.ts** - A unified include file to load all sample states.
    - **config.ts** - A sample settings management class. 
    - **main.ts** - A sample Phaser bootstrap that loads Phaser on page load and begins the boot state.
    - **startup.ts** - A sample entry point for the game.
    - **window.ts** - An interface used to expose JavaScript-based libraries to TypeScript. 
- **www** - All compiled code and static files are housed here for Cordova/PhoneGap to access.

Once `grunt build` has been run, the `www` directory will have the following structure.
 
- **assets** - Copy of the base `assets` directory.
- **js** - All JavaScript files are copied into this directory.
  - **bundle.js** - All TypeScript files are compiled and placed into this singular JavaScript file.
  - **config.js** - A processed copy of the `config.json` file in the root.
  - **jed.js** - Needed for using Jed.  Copied from NPM.
  - **phaser.js** - Needed for using Phaser.  Copied from NPM.
- **index.html** - The same file found under `src/html`.

The following configuration files are provided to ease into the workflow provided by this template.

- **config.json** - Unused at this time.
- **tsconfig.json** - Configuration used when compiling TypeScript code.
- **tslint.json** - Configuration for using TSLint to check for code style mistakes.  Defers to Phaser's recommended settings.
- **typings.json** - Used by the Typings library to provide type-hinting `.d.ts` files in the `typings` directory.
- **webpack.config.js** - Configuration used by webpack to package particular source files.

## Grunt Tasks
You can always use `grunt -h` to list all available tasks.  Below is a list of useful tasks provided by this template.

- **build** - Clears all content out of `www`, then compiles and copies code and assets into the same directory.
- **serve** - Start a server at [http://localhost:9000](http://localhost:9000).  Press `<ctrl>-C` on the command line to stop the task.
- **debug** - Same as `serve`, but provides live reload for the served files. The `watch` task is called to trigger the live reload.  Press `<ctrl>-C` on the command line to stop the task.
- **lint** - Run all linters and code validation tasks.
- **open** - Open [http://localhost:9000](http://localhost:9000) in your default browser.

## License
Copyright 2016 Craig A. Hancock

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

&nbsp;&nbsp;&nbsp;&nbsp;http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
