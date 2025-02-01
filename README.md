# Urban Routes App
**Skills:**
- Exploratory Testing
- Test Design
- Jira
- DevTools
- UI Testing
- Cross-platform Testing
- Requirement Analysis
- Test Case Creation
- Bug Report
- JavaScript
- Node.js
- Test Automation
- WebdriverIO
- Mocha
- Git
- GitHub
## Overview
The Urban Routes Web App helps users find the best ways to travel within a city by providing estimated travel time and cost for various transportation options, including walking, driving, biking, and car sharing. 
The app underwent a significant update, requiring thorough testing of two key features:
- **Carsharing:** an existing feature with newly developed backend logic.
- **Aero Taxi:** a confidential upcoming feature that was not yet visible in the UI but required pre-release testing.

This project involves both **manual and automated UI testing**, focusing on validating the app's functionality to ensure a seamless user experience.
<p float="center">
  <kbd>
<img src="/Screenshots/6.png" alt=" Web App Screenshot" width=70% heigh=70% hspace="140">
  </kbd>
</p>

## Manual Testing

During manual testing, I conducted:
### Requirement Analysis
- Broke down functional requirements into [atomic testable blocks](https://docs.google.com/document/d/13L1qBWeNQmvj-e7gdkkQMLHCLqWPunpVw9k89u2hzFk/edit?usp=sharing).
- Identified critical paths and potential edge cases for the new features.
### Test Case Creation
- Defined [equivalence partitions and boundary values](https://docs.google.com/spreadsheets/d/1GjII_nG-ZjnZpzFb-fPzaKgUezN365x6xZ5i1ztQu8I/edit?usp=sharing) to categorize valid and invalid inputs.
- Created detailed [test cases in Google Sheets](https://docs.google.com/spreadsheets/d/1BF-JXcUfjOkjCj6os2kN8SMcdSnGwp8IbO5EuB0cY7M/edit?usp=sharing), covering:
    - Standard and edge cases for route calculations.
    - Override testing for the hidden Aero Taxi feature.
    - Handling of invalid data inputs in transportation selection.
### Test Execution
- Ran tests manually, identifying gray areas in the requirements.
- Used Chrome DevTools to [override app settings](https://www.youtube.com/watch?v=bfjFYf6esNE&t=62s), enabling pre-release feature validation.
### Bug Reporting in Jira
- Documented [all issues](https://docs.google.com/document/d/1z78yaacN5JCIF8__8KT1KsLRQJGYQef1oJ-39vvqUvI/edit?usp=sharing) clearly and concisely for quick resolution.
- Categorized bugs into UI/UX issues, performance problems, and incorrect route calculations.

## Automated Testing
I wrote automated tests for the whole taxi ordering process, including:
- Address input validation.
- Selecting transportation plans.
- Phone number input and validation.
- Simulating payment method selection (credit card processing).
- Handling UI elements like modals and dropdowns.
### Challenges Overcome:
  - Simulated TAB keypresses to activate the payment button.
  - Verified dynamic UI state changes when adding extras (blanket, handkerchiefs, ice cream).
  - Ensured the car search modal functioned correctly.
  - Tracked the countdown timer for driver assignment in the UI.
 ### Setup
  Before running the tests, ensure the following prerequisites are met:
  - Node.js (LTS version)
  - npm (latest version)
  - WebdriverIO CLI
### Getting Started
  1. Clone the repository to your local machine
  2. Navigate to the project directory
### Configuration
To configure the server URL for the project, modify the baseUrl in the wdio.conf.js file according to your testing server.
These tests support running in headless and non-headless modes with Chrome and Firefox browsers. To change the browser or switch between headless and non-headless modes, update the capabilities section in wdio.conf.js.
### Running the Tests
To execute the tests, run the following command: npm run wdio.
### Test Cases
The test suite includes the following cases with their respective success rates:
1. Setting up addresses
2. Selecting the Supportive plan
3. Filling in the phone number
4. Adding a credit card
5. Writing a message for the driver
6. Ordering a Blanket and handkerchiefs
7. Ordering 2 Ice creams
8. Verifying the car search modal appears
9. Waiting for driver info to appear

These tests are in the createAnOrder.e2e.js file within the test/specs folder.

### Code Style
The project adheres to the following code style conventions:
- ES6 syntax
- Async/Await for handling asynchronous operations
- Descriptive naming conventions for variables and functions
- Consistent indentation (2 spaces)
- Use of single quotes for strings
- Commenting code for clarity where necessary

## Findings
The Urban Routes App is mostly stable, but several critical issues were found in route calculations, carsharing interactions, and UI responsiveness. The Aero Taxi feature was successfully tested via overrides, revealing unresolved navigation and payment flow issues.

### Summary
1. **UI/UX Issues:**
- The carsharing UI did not update correctly when switching between transport modes.
- Some route calculations failed to display estimated costs, affecting usability.
2. **Backend Logic Issues:**
- The Aero Taxi feature could be accessed via Chrome DevTools overrides, revealing:
- Inconsistent pricing calculations for Aero Taxi fares.
- Unresponsive map elements fail to highlight the chosen Aero Taxi pickup point.
3. **Automated Testing Challenges:**
- Payment processing automation required UI interaction simulation, which was difficult to execute reliably.
- Dynamic UI elements (e.g., pop-ups, countdown timers) required special handling in tests.

### Key Areas for Improvement
In my test report, I highlighted several key areas for improvement:
- Fix UI inconsistencies in transport selection, ensuring smooth updates when switching between modes.
- Improve Aero Taxi pricing logic before public release.
- Enhance UI responsiveness in carsharing route selection.
- Optimize automated test execution for complex UI elements.
- Refine map interaction handling to improve user navigation.
