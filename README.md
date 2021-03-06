# Grunt Drupal Tasks
## A Grunt plugin to automate Drupal build and testing tasks

Code Status (master branch):
[![Travis CI status](https://travis-ci.org/phase2/grunt-drupal-tasks.svg?branch=master)](https://travis-ci.org/phase2/grunt-drupal-tasks)
[![Dependency Status](https://david-dm.org/phase2/grunt-drupal-tasks.svg)](https://david-dm.org/phase2/grunt-drupal-tasks)
[![Peer Dependency Status](https://david-dm.org/phase2/grunt-drupal-tasks/peer-status.svg)](https://david-dm.org/phase2/grunt-drupal-tasks#peer-badge-embed)
[![npm version](https://badge.fury.io/js/grunt-drupal-tasks.svg)](https://www.npmjs.com/package/grunt-drupal-tasks)

## Requirements

* Install _Node.js v0.10.0 or better_ either using a
<a href="https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager">package manager</a>
like apt-get, brew, or yum or a
<a href="http://nodejs.org/download/">standalone installer</a>.

* Once _Node.js_ is installed, use _npm_ to install
<a href="https://github.com/gruntjs/grunt-cli">grunt-cli</a>, the Grunt command
line interface, by running:

```
npm install -g grunt-cli
```

* Some optional features, used in the included example and end-to-end test
  suite, require additional tools, including <a href="http://bundler.io/">Bundler</a>,
  <a href="https://getcomposer.org/download/">Composer</a>, Ruby, and RubyGems.

## Quickstart

We have a [Yeoman](http://yeoman.io) generator that can quickly take you from an
empty directory to a running Drupal site using this toolchain.

Please welcome [Gadget](https://github.com/phase2/generator-gadget)!

## Features

This project is built on the tools of the Grunt community to provide scripted
automation of a number of PHP & Drupal tasks. Here are a few examples of what it
provides:

* Drush make-based build workflow
* CI portability (used with Jenkins so far)
* Opt-in for a number of great enhancements:
  * Composer dependency management for PHP
  * Bundler dependency management for Ruby
  * PHP code quality & static analysis checks
  * Compass compilation
  * Behat testing
* Deployment packaging
* Extensibility: Add or override with your plugins or configuration.

We are continuously working to improve this toolchain, adding functionality that
we see as common to our _continuous integration_ and everyday development
practices.

## Usage

Working on a project that's integrated **grunt-drupal-tasks**? Run `grunt help`
to view documentation tailored for your project.

To build your Drupal site, run `grunt`.

### Commands

The following is a list of base commands and their options which you can expect to find on any **grunt-drupal-tasks** based project.

#### Build Process

* `grunt`
  * The default build process, which includes verifying dependencies and assembling the build directory. 
* `grunt scaffold`
  * Apply the scaffolding from src/ to the Drupal docroot. 

#### Operations

* `grunt package`
  * Package the operational codebase in the `/build/packages/` directory for deployment.
  * Use `package:compress` to compress the packaged directory into an archive.
* `grunt serve`
  * Run Drupal using the PHP built-in webserver.
  * Use `serve:demo` to run without watch tasks
  * Use `serve:test` for grunt-drupal-tasks development. 

#### Testing & Code Quality

* `grunt analyze`
  * Run static codebase analysis to detect problems. 
  * Outputs Jenkins-compatible reports. (e.g. PHPMD) 
* `grunt test`
  * Run the Behat tests included with this project. 
* `grunt validate`
  * Quick code health check for syntax errors and basic practices. (e.g. PHPCS w/ Drush Coder rules) 

#### Dependency Management

* `grunt composer`
  * Install dependencies defined in this project's composer.json file.
* `grunt drushmake`
  * Prepare the build directory and run "drush make" 
* `grunt newer`
  * Use "newer:drushmake" to run the drushmake task only if the make file was updated since the last running. 

#### Utilities

* `grunt clean`
  * Remove the build output directory.

#### Asset & Code Compilation
* `grunt compile-theme`
  * Run compilers for all themes (such as Compass).

#### Real-time Tooling

* `grunt watch-test`
  * Watch for changes that should trigger new testing and validation of the codebase. 
* `grunt watch-theme`
  * Watch for changes that should rebuild frontend assets, such as CSS.

### Special Flags

These flags are not yet documented as part of the `grunt help` command.

* `--quiet`: Suppress desktop notifications.
* `--notify`: Request a desktop notification despite timing or environment settings.
* `--timer`: Output execution time profile at the end of the task run.
* `--concurrency`: Override the dynamic concurrency by Drush Make.

### Environment Options

These environment variables will override other options.

* `GDT_DOMAIN`: Specify the base URL for live system testing. Falls back to a
setting in the project's Gruntconfig.json, then hostname if not set.
* `GDT_QUIET`: If evaluated truthy, will suppress all desktop notifications.

## Setting Up and Extending

For information on setting up your project with these tools, see
<a href="https://github.com/phase2/grunt-drupal-tasks/blob/master/CONFIG.md">CONFIG.md</a>.

For information on extending these tools or contributing changes, see
<a href="https://github.com/phase2/grunt-drupal-tasks/blob/master/EXTEND.md">EXTEND.md</a>.

For information on using these tools with a continuous integration (CI) system,
see <a href="https://github.com/phase2/grunt-drupal-tasks/blob/master/CI.md">CI.md</a>.
