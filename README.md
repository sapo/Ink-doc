# Welcome to [Ink](https://ink.sapo.pt) [![Build Status](https://travis-ci.org/sapo/Ink.svg?branch=develop)](https://travis-ci.org/sapo/Ink)

Ink is an interface kit for quick development of web interfaces, simple to use and expand on. It uses a combination of HTML, CSS and JavaScript to offer modern solutions for building layouts, display common interface elements and implement interactive features that are content-centric and user friendly for both your audience and your designers & developers.

Read the full documentation here: [https://ink.sapo.pt](https://ink.sapo.pt)

Checkout our source code or report an issue here: https://github.com/sapo/Ink

## This repository is used for Ink's documentation only
If you find any inaccuracies or problems in our documentation this is the place to get them fixed.


## Installing Jekyll and required build tools

### On Windows

- [Running Jekyll on windows](https://github.com/juthilo/run-jekyll-on-windows/). Read and follow this how-to thoroughly and you'll save yourself hours of frustration.
- [Install node.js](https://nodejs.org/) This is required to run our build scripts.
- Install the [Compass](https://compass-style.org/) ruby gem by running following command on the command line ``gem install compass``
- Install the [grunt-cli](https://github.com/gruntjs/grunt-cli) by running the following command on the command line ``npm install -g grunt-cli``
- Install all other dependencies by running the ``npm install`` command **inside Inks folder**.

------


### On OS X / Linux

- Install [Jekyll](https://jekyllrb.com/) by running this command on a terminal: ``gem install jekyll``
- Install the [Compass](https://compass-style.org/) ruby gem by running following command a terminal ``gem install compass``
- Install the [grunt-cli](https://github.com/gruntjs/grunt-cli) by running the following command a terminal ``npm install -g grunt-cli``
- Install all other dependencies by running the ``npm install`` command **inside Inks folder**.

------

## Getting stuff running

**All these commands must be ran inside Inks folder**

We also have quite a few usefull grunt tasks:

- ``grunt css`` compiles the scss src into css
- ``grunt js`` builds the js portion of ink
- ``grunt docs`` renenerates the js documentation and launch a local instance of the documentation site on http://localhost:4000
- ``grunt jekyll`` launches a local instance of the documentation site on http://localhost:4000
- ``grunt watch`` will watch the src/ folder for changes on eiher js or scss files and rebuild the lot.
- ``grunt watch:js`` will watch the src/ folder for changes on js files and rebuild.
- ``grunt watch:css`` will watch the src/ folder for changes on scss files and rebuild.
