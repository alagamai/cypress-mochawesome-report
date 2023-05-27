# Generate consolidated test report in html format  using mochawesome 

# Prerequisites

The first thing we need to do is to setup our environment. So here are some things that you should have to start this project:

VSCode: https://code.visualstudio.com/download </br>
NPM: https://www.npmjs.com/get-npm </br>
NodeJS: https://nodejs.org/en/download

# Steps to generate mochawesome report:
  1. Install the required packages as dev dependencies:

   - npm install --save-dev mochawesome mochawesome-merge mochawesome-report-generator 

 2. Run your Cypress tests with the Mochawesome reporter. Update your Cypress configuration in cypress.config.js as mentioned before:

     	module.exports = defineConfig({
     
	     e2e: {
   	 	setupNodeEvents(on, config) {
      		// implement node event listeners here
    	     },
    	reporter: 'mochawesome',
    	reporterOptions: {
      		reportDir: 'cypress/reports',
      		overwrite: false,
    	},
    	screenshots: {
		enabled: true,
    	},
  	},
	});

3. Run your Cypress tests using: npx cypress run

4. Merge the individual JSON files into a single JSON file:

- npx mochawesome-merge cypress/reports/*.json > cypress/reports/mochawesome-ALL.json

- This command merges all the individual JSON files into a single mochawesome-ALL.json file.

5. Generate the HTML report from the merged JSON file:

- npx mochawesome-report-generator cypress/reports/mochawesome-ALL.json

- This command generates a single HTML report (mochawesome.html) from the merged JSON file.

- Now you can open the mochawesome.html file in your web browser to view the consolidated report containing results from all the test runs.



## Use

1. Checkout the project from git - git clone https://github.com/alagamai/cypress-mochawesome-report
2. Navigate to the project root directory - cypress-mochawesome-report
3. Install dependencies with `npm install` 
4. execute 
   npm run cy:run - to run npm scripts in headless mode 
   
   npm run cy:merge-json - to merge all jsons into single consolidated json file
   
   npm run cy:group-html - to convert merged json into consolidated html report   
    

