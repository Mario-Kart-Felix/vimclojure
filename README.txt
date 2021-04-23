___    ______           ______________     ________
__ |  / /__(_)______ _____  ____/__  /___________(_)___  _____________
__ | / /__  /__  __ `__ \  /    __  /_  __ \____  /_  / / /_  ___/  _ \
__ |/ / _  / _  / / / / / /___  _  / / /_/ /___  / / /_/ /_  /   /  __/
_____/  /_/  /_/ /_/ /_/\____/  /_/  \____/___  /  \__,_/ /_/    \___/
                                           /___/

VimClojure – a Clojure environment for Vim
==========================================

VimClojure is one of the most sophisticated editing environments for Clojure.
It provides syntax highlighting, indenting and command completion.

If requested it also provides a SLIME like interface to dynamically work with
Clojure code. For this to work the included Nailgun server must be running.
Remote may be forwarded via ssh.

Features of the interactive interface are:

- dynamic documentation lookup
- dynamic javadoc lookup (in an external browser)
- Repl running in a Vim buffer
- smart omni completion
- easy evaluation of code in a buffer

To activate the interactive interface define the clj_want_gorilla variable
in your .vimrc: let clj_want_gorilla = 1

Requirements
============

Please make sure that the following options are set in your .vimrc:

––8<––––8<––––8<––
syntax on
filetype plugin indent on
––8<––––8<––––8<––

Otherwise the filetype is not activated, and hence VimClojure doesn't work.

Building the Nailgun interface
==============================

To build the Nailgun interface, create a local.properties file that contains
the path to your clojure.jar and clojure-contrib.jar. The file should look
similar to:

––8<––––8<––––8<––
clojure.jar=/path/to/clojure.jar
clojure-contrib.jar=/path/to/clojure-contrib.jar
nailgun-client=ng
vimdir=/custom/installation/path/for/vimplugin
––8<––––8<––––8<––

Once you have created this file, simply run ant. This should give a
vimclojure.jar containing the server part and the nailgun client. Note for
Windows users: please leave out the last line in the properties file. The
windows client for nailgun is included in the distribution as ng.exe. Delete
it only in case you are sure, that you can rebuild it. You may see an error
when building the nailgun-client. That's ok.

Running „ant install“ will install the vim plugin into the named directory.
If you omit the vimdir line in the local.properties file the vim plugin
will be installed in the user's runtime directory – <home>/.vim on Unic/Mac,
<home>\vimfiles on Windows.

To run the Nailgun server you need the clojure.jar, clojure-contrib.jar and
vimclojure.jar in your Classpath:

java -cp /path/to/clojure.jar:/path/to/clojure-contrib.jar:/path/to/vimclojure.jar com.martiansoftware.nailgun.NGServer 127.0.0.1

There is also a launcher script included in the bin subdirectory based on
Stephen C. Gilardi's clj-env-dir launcher. Set the environment variable
CLOJURE_EXT to the name of a directory containing the jars and (possibly
links to) subdirectories you want in your classpath. Additionally the
CLASSPATH environment variable will be added to the classpath.

Put the nailgun client somewhere into your PATH or specify the location in
your .vimrc by means of the vimclojure#NailgunClient variable.

––8<––––8<––––8<––
let vimclojure#NailgunClient = "/path/to/your/ng"
––8<––––8<––––8<––

Please refer to the online documentation in the doc folder for further
information on how to use VimClojure, its features and its caveats.

Note: You might need to check the Makefile for special lib requirments
to compile the nailgun client, eg. OpenSolaris.

Using Ivy
=========

Alternatively you may use Ivy to resolve the dependencies. Simply omit the
first two lines in the local.properties file and ant will automatically
download any missing dependencies. In case you don't have Ivy installed,
this will be fetched also.

VimClojure is available as Ivy dependency also. Run "ant publish-local"
after building the VimClojure and use

    <dependency org="de.kokta" name="vimclojure" rev="2.1.0"/>

to include the VimClojure jar in your projects classpath. But mapping
the dependency to a private configuration the dependency is only for
development. Users of your project won't be bothered with the dependency.
# typescript
README.md
typescript-action status

Create a JavaScript Action using TypeScript
Use this template to bootstrap the creation of a TypeScript action.🚀

This template includes compilation support, tests, a validation workflow, publishing, and versioning guidance.

If you are new, there's also a simpler introduction. See the Hello World JavaScript Action

Create an action from this template
Click the Use this Template and provide the new repo details for your action

Code in Main
Install the dependencies

$ npm install
Build the typescript and package it for distribution

$ npm run build && npm run package
Run the tests ✔️

$ npm test

 PASS  ./index.test.js
  ✓ throws invalid number (3ms)
  ✓ wait 500 ms (504ms)
  ✓ test runs (95ms)

...
Change action.yml
The action.yml contains defines the inputs and output for your action.

Update the action.yml with your name, description, inputs and outputs for your action.

See the documentation

Change the Code
Most toolkit and CI/CD operations involve async operations so the action is run in an async function.

import * as core from '@actions/core';
...

async function run() {
  try { 
      ...
  } 
  catch (error) {
    core.setFailed(error.message);
  }
}

run()
See the toolkit documentation for the various packages.

Publish to a distribution branch
Actions are run from GitHub repos so we will checkin the packed dist folder.

Then run ncc and push the results:

$ npm run package
$ git add dist
$ git commit -a -m "prod dependencies"
$ git push origin releases/v1
Note: We recommend using the --license option for ncc, which will create a license file for all of the production node modules used in your project.

Your action is now published! 🚀

See the versioning documentation

Validate
You can now validate the action by referencing ./ in a workflow in your repo (see test.yml)

uses: ./
with:
  milliseconds: 1000
See the actions tab for runs of this action! 🚀

Usage:
After testing you can create a v1 tag to reference the stable and latest V1 action<mb@kotka.de>
Frankfurt am Main, 2009
