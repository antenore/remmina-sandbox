How to manage versions in the Remmina project
=============================================

This document describes how versioning is managed in Remmina project.

Goals
-----

 * start to use `major`, `minor` and `revision` values
 * Ubuntu: manage nightly build and official build in a consistent way, allowing switch between repositories


Upstream version
----------------

It is what appear in the `About` of remmina, not related to a specific distribution.

Is composed as:

`<major>` . `<minor>` . `<revision>` `<suffix>`

where `<suffix>` could be something like: 
  * a letter or a plus (`+`) or a period (`.`) followed by alphanumerical characters that mean: 

    _this version follow the same version without suffix_
  * an alphanumeric suffix starting with tilde caracter (`~`) that mean:

    _this version preceding the same version without suffix_.

Ubuntu stable version
---------------------

`<major>` . `<minor>` . `<revision>` `<suffix>`-0ubuntu`<ubuntu_num_suffix>`~`<ubuntu_serie_nickname>`

**e.g.**: `1.2.1d-0ubuntu1~trusty`

Ubuntu development version
--------------------------
`<major>` . `<minor>` . `<revision>` `<suffix>`~dev`<revtime>`-0ubuntu0~git`<git-commit>`

where:

  * `<revtime>` is the date and time of the current commit
  * `<git-commit>` is the first 7 characters of the hash of the current commit

**e.g.**: `1.2.1~dev201608190612-0ubuntu0~git3835f9f~ubuntu16.04.1`

Development workflow
--------------------
When a new stable version is released the master branch must be updated to the next release candidate,
in this way until the next version will be released the development (nightly) builds will be further the current stable release but behind the next stable release.