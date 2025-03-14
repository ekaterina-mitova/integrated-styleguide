# Intelligent Integrated Style Guide

This project is an implementation of an intelligent integrated style guide. 
A modern style guide has a number of features that distinguish it from a traditional style guide, such as:

* **discoverable** - the writer can discover style guide rules as s/he writes
* **enforceable** - the writer is notified automatically when rules are not followed
* **interactive** - the writer is assisted to fix the detected issues
* **dynamic** - the style guide evolves in time, writers being able to propose updates/changes

This project uses the following technologies:

* DITA
* XSLT
* Schematron
* Schematron Quick Fix

The style guide source is XML/DITA and it can be found in the `src` folder, as a DITA map and DITA topics. Along with the prose, the style guide topics contain also information that can be used to automate the style guide checks, let's call these **automated rules**.

An **automated rule** is an instantiation of a **generic rule**, by providing values for the generic rule parameters. The generic rules are defined in our case as Schematron abstract patterns in a library of rules, found in `src/rules/library.sch`. 

The style guide is published automatically by a continuous integration server (Travis) and made accessible through GitHub Pages at https://ekaterina-mitova.github.io/integrated-styleguide. 

If you want to add a new rule, follow the *Edit online* link on each topic and then once you insert a new paragraph you will be offered with the option to either type content or add a rule. If you choose to add a rule then you will be able to select one of the generic rules and then add its parameters and fill in their values to obtain the desired constraint. Saving the topic will allow you to send your change as a pull request and if that is accepted and your change gets committed on the repository then the style guide will be automatically republished. 

The automated rules are also made available and updated every time the style guide is published, they are available at https://ekaterina-mitova.github.io/integrated-styleguide/rules/rules.sch.

Create your own style guide
---------------------------

To get the same functionality under your account, you need to follow the steps below:

- Fork the project
- Under the *Settings* tab of your project in GitHub make sure the *GitHub Pages* section says
  ```Your GitHub Pages site is currently being built from the gh-pages branch.```
- Go to [Travis website](http://travis-ci.org) and use the *Sign in with GitHub* action then authorize Travis to access your account - this is needed to enable automatic publishing of the style guide
- Identify then the forked repository and activate it using the *Activate repository* action
- Under *More options*->*Settings*  
    - Enable *Build only if .travis.yml is present*
    - Disable *Build pull requests*
    - Define the GH_TOKEN variable under *Environment Variables* by setting its value to a GitHub Token that you can generate from GitHub in order to enable Travis to commit on your GitHub repository, it needs to commit on the *gh-pages* branch.
To obtain that value, you need to go to *GitHub* and under *Settings* / *Developer settings* there is a *Personal access tokens* section. Use the *Generate new token* button to generate a token and enable the options under the *repo* category. Copy the token value and use it to define the value of the *GH_TOKEN* variable
    - Define the WEBHELP_LICENSE variable under *Environment Variables* by setting its value to the oXygen Webhelp license key, eclosed in quotes - this will be used by the publishing process to build the webhelp output. You can obtain a trial license from 
[http://oxygenxml.com/xml_webhelp/register.html](http://oxygenxml.com/xml_webhelp/register.html)  

- You need to push some changes to GitHub on the *master* branch to force an initial build or force a build directly from Travis.

- Check on the Travis website and see when the build is finalised, then your project GitHub Pages will be up-to-date and you can access your styleguide.

## Note
The GitHub Pages URL where you can see this style guide is 
https://ekaterina-mitova.github.io/integrated-styleguide
If you forked the project then the URL needs to be updated to contain your user name and your project name.

Test
---------------------

You can [open a sample test file](https://www.oxygenxml.com/oxygen-xml-web-author/app/oxygen.html?url=https://github.com/ekaterina-mitova/integrated-styleguide/blob/master/test/sample-direct-ref-schema.dita) in [oXygen XML Web Author](https://www.oxygenxml.com/xml_web_author.html).


Copyright and License
---------------------
Copyright 2018 Syncro Soft SRL.

This project is licensed under [Apache License 2.0](https://github.com/oxygenxml/integrated-styleguide/blob/master/LICENSE)
