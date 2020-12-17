# UI

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.5.3.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).



## Build for mobile application

       Step 1: Pull the latest code from bitbucket.
       Step 2: Change in .angular-cli.json file. Made outDir: “www”. for cordova mobile app build
       Step 3: Run : ng --build --base-href (This will create www folder)
       Step 4: Cordova add platform android (This will generate plugin and platform folder) 
        Note: If folder are already there don't run.
       Step 5: Cordova run android 


