# kursausschreibung 3.4.0
[![Build 🏭🚀](https://github.com/bkd-mba-fbi/kursausschreibung/actions/workflows/buildDeploy.yml/badge.svg)](https://github.com/bkd-mba-fbi/kursausschreibung/actions/workflows/buildDeploy.yml)

# Documentation
Go to the [Wiki](https://github.com/bkd-mba-fbi/kursausschreibung/wiki)

# How to implement in your page?

## Configuration (appconfig, settings, locale)

* **appconfig:** The basic configuration for the module must be stored in appconfig. Example: `apiUrl, webBaseUrl, oauthUrl, instanceId, clientId, applicationScope`
* **settings:** In this file you will find all settings for the module.
* **locale:** In the 'locale' folder you will find every translation for the module that does not come from Evento (e.g. labels, status, process...).

## Builds

You can download releases on the [releases page](https://github.com/bkd-mba-fbi/kursausschreibung/releases) and the latest build of the module here: [kursausschreibung.zip](https://bkd-mba-fbi.github.io/kursausschreibung/kursausschreibung.zip). To use the module you first have to configure it.

## Integration

For the integration into an html page you need a simple html configuration in header and body of the page in which you want to publish the module. Please see section `MODULE head configuration` and `MODULE MAIN APPLICATION` in `index.html`.

If you want to be sure that after authentication by the module the correct address is always used use `OPTION REDIRECT` in the `index.html` [GoTo](https://github.com/bkd-mba-fbi/kursausschreibung/blob/master/app/index.html). Please put script element between head and body of main page (load faster).

# For Development 
## Prerequisites

You will need the following things properly installed on your computer.

* [Git](https://git-scm.com/)
* [Node.js](https://nodejs.org/) (with npm)
* [Ember CLI](https://ember-cli.com/)
* [Google Chrome](https://google.com/chrome/)

## Installation

* `git clone https://github.com/bkd-mba-fbi/kursausschreibung.git`
* `cd kursausschreibung`
* `npm install`
* `cd node_modules/uikit`
* `npm install`
* `npm run scope` (make sure node is up to date)

### Problem npm install
For one reason or another, some people can't connect to the registry via HTTPS. This can be fixed by setting the registry to use HTTP instead:

* `npm config set registry http://registry.npmjs.org/`
* `npm config set strict-ssl false`

## Running / Development

* `ember serve`
* Visit your app at [http://localhost:4200](http://localhost:4200).
* Visit your tests at [http://localhost:4200/tests](http://localhost:4200/tests).

### Code Generators

Make use of the many generators for code, try `ember help generate` for more details

### Running Tests (tests not yet implemented)

* `ember test`
* `ember test --server`

### Linting

* `npm run lint:js`
* `npm run lint:js -- --fix`

### Building

* `ember build` (development)
* `ember build --environment production` (production)

## Further Reading / Useful Links

* [ember.js](https://emberjs.com/)
* [ember-cli](https://ember-cli.com/)
* Development Browser Extensions
  * [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
  * [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)

## Documentation
Go to the [Wiki](https://github.com/bkd-mba-fbi/kursausschreibung/wiki)

## Configuration (appconfig, settings, locale)

* **appconfig:** The basic configuration for the module must be stored in appconfig. Example: `apiUrl, webBaseUrl, oauthUrl, instanceId, clientId, applicationScope`
* **settings:** In this file you will find all settings for the module.
* **locale:** In the 'locale' folder you will find every translation for the module that does not come from Evento (e.g. labels, status, process...).

## Builds

You can download releases on the [releases page](https://github.com/bkd-mba-fbi/kursausschreibung/releases) and the latest build of the module here: [kursausschreibung.zip](https://bkd-mba-fbi.github.io/kursausschreibung/kursausschreibung.zip). To use the module you first have to configure it.

## Integration

For the integration into an html page you need a simple html configuration in header and body of the page in which you want to publish the module. Please see section `MODULE head configuration` and `MODULE MAIN APPLICATION` in `index.html`.

If you want to be sure that after authentication by the module the correct address is always used use `OPTION REDIRECT` in the `index.html` [GoTo](https://github.com/bkd-mba-fbi/kursausschreibung/blob/master/app/index.html). Please put script element between head and body of main page (load faster).

# STUBR FORK

This is a fork for bff with the following custom additions

- eventEnded in date-helpers.js returns false for events without end date (PR sent)
- inputs have a class indicating the input type for better styling (checkboxes)

## Archive
These changes have had a PR which was accepted and are now in upstream
- Bumped softwareversion in package.json to 3.3.0 (PR accepted)

## Workflow

We use the following workflow to maintain our codebase and get updates from upstream.

Our `develop` follows upstream/develop.
Our `master` follows upstream/master.

There is a branch called `upstream` which follows upstream/develop. We cherrypick commits into this branch to create pullrequests to upstream.

For example we made a correction `f4d27e04b` in our develop branch. We want to give this commit back to upstream.

For that we change into our `upstream` branch, cherry pick our commit `git cherry-pick f4d27e04b` and create a pull-request.
Now they can decide whether they want the change or not.

## Ember / Build

Our build process is the same as the normal build process:

* `ember build` (development)
* `ember build --environment production` (production)

We then copy the created files into the bff-web repository for testing/production

## Merging Upstream

Before we build a new release we want to merge all changes from upstream.

* `git fetch upstream`
* `git merge upstream/develop` for develop
* `git merge upstream/master` for master

Resolve conflicts if existing and commit.

## Releases / Tags

If we have a version which we want to release, we create a new tag after building the version.
We have a very simple version numbering scheme: VERSION_UPSTREAMVERSION
For example `1_3.3.1`

Example:
`git tag -a v1_3.3.1 -m "STUBR Version 1, ref upstream v3.3.1"`
Push your newly created tag to origin
`git push origin --tags`
