---
layout: essay
type: essay
published: true
title: DannyWOD - Form Extension
date: 2017-10-17
labels:
  - WOD
---

# DannyWOD: Form Extension

For this DannyWOD, you will modify meteor-example-form so that the Create Student Data page will also have a selection box in which students can select the year that they are planning to graduate.  You will then test this selection box by adding a new student and viewing the document within Mongo.  Here is an example of the extra selection box:

## The WOD

Ready? Let's begin:

### Run meteor-example-form

 1. Create a GitHub repository called form-extension and clone it to your local file system.

 2. Import the [meteor-example-form](https://github.com/ics-software-engineering/meteor-example-form/) code into your local form-extension repo:

    * Download the zip version of meteor-example-form and extract everything but the README.md file into form-extension.
    * cd into form-extension/app and run `meteor npm install`.
    * Then run `meteor npm run start`.
    * Direct your browser to localhost:3000 to test that the application runs correctly

 3. Create a "Static Web" Intellij project called form-extension that points to your repo.

 4. Set up your project to use our [Javascript coding standards](../coding-standards/reading-javascript-coding-standards.html). In a nutshell:
   
    * Select the [ics-se-code-style.xml]({{ site.baseurl }}/morea/development-environments/ics-se-code-style.xml) preferences template (Preferences > Editor > Code Style).
    * Disable IntelliJ Javascript Inspections (Preferences > Editor > Inspections > Javascript).
    * Define the Javascript Language as ECMAScript6 (Preferences > Languages & Frameworks > Javascript)
    * Enable ESLint (Preferences > Languages & Frameworks > Javascript > Code Quality Tools > ESLint). Specify the ESLint package as the one occurring in app/node_modules/eslint.

### Add working selection box to form

 1. Modify /ui/pages/create-student-data-page.html:

    * Reference another Select\_Form\_Control template, which goes after the *Majors* select form template.  Add label="Grad Year", options=years, and an error message. 

 2. Modify /ui/pages/create-student-data-page.js:

    * In the section with the form field structures (arrays with labels), export a const named *yearList* which contains the strings '2017', '2018', and '2019'.
    * Add a helper function called *years* which maps a label to each year in *yearList*.
    * Within the events section, add a const named *year* which retrieves the user selection when the form is submitted.
    * In *newStudentData*, add *year* to the end of the list.

 3. Modify /api/studentdata/studentdata.js:
    
    * Add a key *year* to the schema, with label set to 'Year' and type set to String.  

### Test the new selection box

 1. Your form should now show a selection box with the label *Grad Year*, and dropdown options of 2017, 2018, and 2019.  

 2. Fill out and submit the form, making sure to select a graduation year.  Do not do any further edits at this time.

 3. In the app directory, run `meteor mongo` and use `db.StudentData.find()` to check that your submitted document is present, along with the year key.  

### Save your changes to GitHub.

 1. Once you’ve finished, commit your changes to GitHub, and check to see that your changes are there.

 2. Raise your hand to notify me that you are done.

{% include wod-times.html Rx="< 15 min" Av="15 - 25 min" Sd="25 - 35 min" DNF="35+ min" %}

