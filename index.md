# Where's My Item?
![ci-badge](https://github.com/wheres-my-item/project/workflows/wheres-my-item/badge.svg)

## Table of contents

* [Overview](#overview)
* [Goals](#goals)
* [System](#system)
* [User Guide](#user-guide)
* [Deployment](#deployment)
* [Community Feedback](#community-feedback)
* [Developer Guide](#developer-guide)
* [Development History](#development-history)
* [Team](#team)

## Overview

'Where's My Item?' is a site designed to allow the UH Manoa Lost Item office to list the many lost items that have been found on campus. Students who have lost something can search the site to look to see if they have something that belongs to them, and file a claim for that item if so. Admin can then verify their claim's authenticity using the information provided to them in a claim form.

The site in itself uses:
- Meteor for Javascript-based implementation of client and server code
- React for component-based UI implementation and routing
- React Bootstrap CSS Framework for UI design

The site contains:
- A landing page that informs new users of the purpose of the site, and prompts them to log-in or sign-up to browse the lost items database.
- A "Found Items" page that shows all the lost items in the database, which users can browse for their own lost item.
  - Each item has pertinent descriptions, such as when it was found, what type of item it is, color, and a basic description.
  - Each item has the option to "Claim This Item". Upon selection, it will take them to a "Claim Item" form where they can submit information that they can use to verify their ownership of the item and their contact information.
- An 'Admin' page that is only available to accounts with admin privileges. Here, there are two sections, "Claimed Items" and "Unclaimed Items". 
  - "Claimed Items" contains items that users have submitted a claim form for, where they can go to verify their identity and decide whether to accept the claim.
  - "Unclaimed Items" contains all the items in the database with no claims submitted for it yet.
  - All items have an "Edit" button that can be used to edit the item in the database.
  - Admins also have the option called "Add Item", where they can use an "Add Stuff" form to add a new item to the database.
- A Log-In and Sign-Up page for users to login or create accounts, which is necessary before they can submit items.
    - This adds to a collection that consists of user accounts, which have fields for the username, password, whether it has admin priveleges, etc.

## Goals

To provide a site for the UH Manoa Lost Item office to list their collection of lost items that have been turned into them, and for students to view said collection to determine if something they've lost is there, and if so, to submit a claim to get back said item.

## System

* Landing Page for first time users
* Sign in and Sign up page
* Home page after Sign in
* Page where you can access all items lost with:
    * Picture
    * Item description
    * Name
    * Where it was found
* Page where you can claim items
* Admin page
* Edit items page for Admins
* Option to delete items that you’ve reported/found if returned to owner for Admins

## Deployment

We used Digital ocean to deploy our web application.

You can view our deployed application <a href="https://uh-manoa-lost-and-found.online/">here</a>!

## User Guide

#### Landing Page

Landing page for users accessing the site without an account:

<div class="center"><img src="doc/landing-page-mockup.png" alt="landing page" width="950px"></div>

Provides information regarding the functionality of the site to the user, and prompts them to login/sign up.

#### User login and signup page

A simple login and singup page:

<div class="center"><img src="doc/sign-in-page-mockup.png" alt="user page" width="950px"></div>

<div class="center"><img src="doc/sign-up-page-mockup.png" alt="user page" width="950px"></div>

This allows users of the website to create accounts and access user specific information.

#### User (after Login) page, non-Admin user

Once you log in (either to an existing account or by creating a new one), the navbar changes as follows:

<div class="center"><img src="doc/user-page.png" alt="user page" width="950px"></div>

You can now access the lost item list and the claim form.

#### Found Items page

Following the navbar link to Found Items will bring you to the page listing all the items that have been found:

<div class="center"><img src="doc/found-items-mockup.png" width="950px"></div>

The items are listed in cards, with images and details. There is also an option to filter (e.g. by category) and to sort (e.g. by date posted). At the bottom of each item card is a link to claim the item. This link leads to the claim form.

#### Claim Form page

The claim form page can be accessed by clicking the link at the bottom of each item card on the Found Items page.

<div class="center"><img src="doc/claim-form-page.png" width="950px"></div>

The claim form page includes the card of the item being claimed. It also has a form for the user to fill in, with their contact information and details about the item. The user can also add a comment. There is also an option to view pending claims.

#### Admin page

The admin page can be accessed after logging in as an admin user, using the navbar.

<div class="center"><img src="doc/admin-page-mockup.png" width="950px"></div>

The page allow you to view all lost items, along with their details. There are two rows of item cards, those with claims and those without claims. Each row is contained in a collapsable container to reduce screen clutter if there are many items.


#### Admin Add/Edit page

The add and edit item pages can be accessed from the admin page. There is a single button to add an item. Each item card has an edit link.

<div class="center"><img src="doc/admin-add-item-page-mockup.png" width="950px"></div>

These pages allow the admin to create/edit an item's image, name, location found, and description. The edit page has an aditional button to delete the item in the case that it was mistakenly added or has been returned to the owner.

## Community Feedback



## Developer Guide

This section provides information of interest to Meteor developers wishing to use this code base as a basis for their own development tasks.


### Installation

First, [install Meteor](https://www.meteor.com/install).

Second, visit the [our application github page](https://github.com/wheres-my-item/project), and click the "Use this template" button to create your own repository initialized with a copy of this application. Alternatively, you can download the sources as a zip file or make a fork of the repo.  However you do it, download a copy of the repo to your local computer.

Third, cd into the project/app directory and install libraries with:

```
$ meteor npm install
```

Fourth, run the system with:

```
$ meteor npm run start
```

If all goes well, the application will appear at [http://localhost:3000](http://localhost:3000).

### Application Design

This project is based upon [meteor-application-template-react](https://ics-software-engineering.github.io/meteor-application-template-react/) and [meteor-example-form-react](https://ics-software-engineering.github.io/meteor-example-form-react/). Please use the videos and documentation at those sites to better acquaint yourself with the basic application design.

### Data Model

Our website contains collections for the user accounts, with fields such as the name of the email, password, and role, the lost items, with fields for the description of the item, and for the claims, with fields describing who is attempting to claim the lost item and proof that they owned it. The claim form links back to the item that the user is attempting to claim.

### Initialization

The config directory is intended to hold settings files. The repository contains one file: config/settings.development.json.

This file contains default definitions for the user accounts, the lost items in the database, and the user claims for a particular item, and the relationships between them.

### Quality Assurance

#### ESLint

The project includes a .eslintrc file to define the coding style adhered to in this application. You can invoke ESLint from the command line as follows:
 
```
meteor npm run lint
```

Here is sample output indicating that no ESLint errors were detected:

```
$ meteor npm run lint

> project@ lint /Users/philipjohnson/github/wheres-my-item/project/app
> eslint --quiet --ext .jsx --ext .js ./imports ./tests

$
```

ESLint should run without generating any errors.

It's significantly easier to do development with ESLint integrated directly into your IDE (such as IntelliJ).

#### End to End Testing

Wheres-my-item uses [TestCafe](https://devexpress.github.io/testcafe/) to provide automated end-to-end testing.

The wheres-my-item end-to-end test code employs the page object model design pattern.  In the [project tests/ directory](https://github.com/wheres-my-item/project/tree/main/app/tests), the file [tests.testcafe.js](https://github.com/wheres-my-item/project/blob/main/app/tests/tests.testcafe.js) contains the TestCafe test definitions. The remaining files in the directory contain "page object models" for the various pages in the system (i.e. Home, Landing, Interests, etc.) as well as one component (navbar). This organization makes the test code shorter, easier to understand, and easier to debug.

To run the end-to-end tests in development mode, you must first start up a wheres-my-item instance by invoking `meteor npm run start` in one console window.

Then, in another console window, start up the end-to-end tests with:

```
meteor npm run testcafe
```

You will see browser windows appear and disappear as the tests run.  If the tests finish successfully, you should see the following in your second console window:

```
PS C:\Users\name\github\project\app> meteor npm run testcafe       

> meteor-application-template-react@ testcafe C:\Users\name\github\project\app
> testcafe chrome tests/*.testcafe.js

 Running tests in:
 - Chrome 119.0.0.0 / Windows 11

 meteor-application-template-react localhost test with default db
 √ Test that landing page shows up
 √ Test that signin and signout work


 2 passed (17s)
```

All the tests pass, but the first test is marked as "unstable". At the time of writing, TestCafe fails the first time it tries to run a test in this mode, but subsequent attempts run normally. To prevent the test run from failing due to this problem with TestCafe, we enable [testcafe quarantine mode](https://devexpress.github.io/testcafe/documentation/guides/basic-guides/run-tests.html#quarantine-mode).

The only impact of quarantine mode should be that the first test is marked as "unstable".

### From Mockup to Production

One additional security-related change that was implemented was the use of https so that the information that flows between the server and the browser is encrypted, which includes confidential information such as logins and passwords.

### Continuous Integration

![ci-badge](https://github.com/wheres-my-item/project/workflows/wheres-my-item/badge.svg)

This site uses GitHub Actions to automatically run ESLint and TestCafe each time a commit is made to the default branch. You can see the results of all recent “workflows” at https://github.com/wheres-my-item/project/actions.

The workflow definition file is located at .github/workflows/ci.yml. 

## Development History

The development process for our website, Where's My Item, conformed to Issue Driven Project Management practices. In short:

* Development consists of a sequence of Milestones.
* Each Milestone is specified as a set of tasks.
* Each task is described using a GitHub Issue, and is assigned to a single developer to complete.
* Tasks should typically consist of work that can be completed in 2-4 days.
* The work for each task is accomplished with a git branch named “issue-XX”, where XX is replaced by the issue number.
* When a task is complete, its corresponding issue is closed and its corresponding git branch is merged into master.
* The state (todo, in progress, complete) of each task for a milestone is managed using a GitHub Project Board.

The following sections document the development history of our project.

### Milestone 1 : Mockups and Initial Page Deployment

Our goal for Milestone 1 was to create our home page, with mockups of what our final website should look like, and an initial deployment of our website with a landing page.

Milestone 1 was managed with [Our GitHub Project Board M1](https://github.com/orgs/wheres-my-item/projects/1):

![](doc/project-board-1.png)

### Milestone 2 : Functionality and Quality

Our goal for Milestone 2 was to work on the functionality and quality of our website, specifically making sure each of our pages work as intended.

Milestone 2 was managed with [Our GitHub Project Board M2](https://github.com/orgs/wheres-my-item/projects/3):

![](doc/project-board-2-update.png)

### Milestone 3 : Functionality and Design

Our goal for Milestone 3 was to further work on the functionality of the website, finishing any unfinished pages from the Milestone 2. In addition to this, we focused on the design and stylization elements of our site. We also asked for community feedback to further improve our project.

Milestone 3 was managed with [Our GitHub Project Board M4](https://github.com/orgs/wheres-my-item/projects/4/views/1):

![](doc/project-board-3.png)

## Team

#### Project Team Member:
- Dao McGill       | dmcgill@hawaii.edu   | [GitHub Profile](https://github.com/daomcgill)
- Michael Nakagawa | mnakaga4@hawaii.edu  | [GitHub Profile](https://github.com/mnakagawa14)
- Riki Macmillan   | rikimacm@hawaii.edu  | [GitHub Profile](https://github.com/rikimacmillan)
- Sean Umeda       | sumeda21@hawaii.edu  | [GitHub Profile](https://github.com/Sumeda21)
- Tiffany Ngo      | ngotiff@hawaii.edu   | [GitHub Profile](https://github.com/tiffany-ngo)

Take a look at our <a href="https://docs.google.com/document/d/15k7QCJ0w4ZB97Gaa42dbeFSXAgJNJC7keOgySTGZSys/edit?usp=sharing">team contract</a>.



