# prototype-kit-template

## Project overview

This prototype provides an early proof of concept for the DAP Inventory, allowing us to explore design ideas, gather user feedback, and test potential user journeys before committing to full development. 

## Installation instructions

Install the dependencies:
`yarn install`

Preview the prototype by running `yarn start`.

## Usage Guides
### How do the build commands work?

This project uses [gulp](https://gulpjs.com/) to automate the above commands. The [prototype kit]({{PROTOTYPE_KIT_HOMEPAGE}}) provides default gulp tasks which are used by this repository which are inherited in the `./gulpfile.js` script.

Additional gulp tasks can be added to this project's `gulpfile.js` in the usual way. Refer to the gulp documentation for information on how to do this.

### Adding gulp tasks

Some example tasks has been added to the gulp.js file for reference.

Do the following after adding in a task:

1. Go to the package.json file. Under the scripts section, Add in the build script name. for example `"build-static-files": "gulp prototype-kit:build-static-files"`
2. In your terminal, run "yarn 'build script name'" for example "yarn build-static-files"

### Developing with a specific version of the design system

Begin by adding a reference to the specific design system version in the `package.json` file of this repository; for example, if version 66.0.0 were required then this would look like this:

```json
"dependencies": {
  "@ons/design-system/66.0.0": "npm:@ons/design-system@66.0.0",
  ...
}
```

Then add the `version` attribute at the top of each Nunjucks template that requires this specific design system version:

```nunjucks
---
version: 66.0.0
---
<p>This page uses design system version 66.0.0.</p>
```

### Additional class attributes

Certain functions have been integrated into the form summary to accommodate specific use cases:

- You can hide a question from summary by assigning the "js-question-no-summary" class to the form element on the page.
- You can return a multi line answer by assigning the "js-multiple-line-answer" class to the form element on the page.

#### Custom JavaScript

If you need to add custom JavaScript, the build system will automatically look for a file called `index.js` in your prototype. Gulp will convert your JavaScript to ES5 code. You can refer to the example folder to see how to include the JavaScript in your template.

#### Custom CSS

If you need to add custom CSS to style a new component or override styling on an existing component you can create a `.scss` file in the directory of your prototype. Gulp will spit out a `.css` file named the same as any `.scss` file that isn't prefixed with an underscore. You can refer to the example folder to see how to include generated css in your template.

#### Linking JSON file to the Autosuggest component

 Follow these steps to correctly link the JSON file to the autosuggest component:

1. Place the JSON file inside the `/src/prototypes/example/data/` folder.  

2. Use **Example 3** in `gulpfile.js` to define a new Gulp task, `build-json`, that copies the JSON file to the `build/` folder.  

3. Add `"build-json": "gulp build-json"` to the script section in `package.json`

4. Run the Gulp Task using `yarn build-json`. This ensures that the JSON file is correctly placed in the build/ folder.

5. When using the autosuggest component, ensure that you reference the correct path for the autosuggestData param. The path should be `data/<json-filename>`

 Note-: When deploying the prototype, create a new public gist at https://gist.github.com/ and add the Json file using .json extension. Then, click on 'raw' button and copy the URL into the autosuggestData param.
 
