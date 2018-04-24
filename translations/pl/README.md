# FreeCAD-documentation

This is an experiment to reconstruct the FreeCAD documentation in a more sustainable, markdown-based way. It is, at the moment, solely made to serve as a proof-of-concept, to explore what is possible to do with markdown files and a git-based system, test different functionalities and systems in order to get to the same level of efficiency and openness we have on the FreeCAD wiki, and ultimately, if all goes well, convince the community to make the switch.

## Goals

* Have a more structured, professional-looking and easy to navigate and use documentation than we currently have on the wiki
* Be more easily manageable, "backupable" and portable than the current wiki
* Be easier to pack in an offline documentation package to be bundled with FreeCAD
* Offer the same level of easiness to people wanting to collaborate
* Offer a good translation system that is easy to use for peeople wanting to translate
* Offer documentation ‘versions’ that correspond to FreeCAD releases
* Offer documentation in formats suitable for offline readers - ePub, pdf, etc.
* Example files could be integrated here too

## TODO

1. [ ] Define a better structure than the user hub / power user hub / developers hub of the wiki? Are these hubs entirely necessary? The wiki structure is "flat" (all pages are at the same level, and can be part of categories), the directory structure of git can allow something more structurated
2. [ ] Define how to cope with the command reference. This is the main subject of the offline doc, it should be handled with extra importance. Also find a way to identify missing command pages, etc...
3. [x] Link with docbook (will create the "book workflow" + pdf, ebook... automatically). Basically need to update <SUMMARY.md> DONE - https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation
4. [x] Check how translation systems can handle this: crowdin (preferred), transifex? Both support md files, check what would be easier to manage (ideally something automatic?) DONE - https://crowdin.com/project/freecad-documentation
5. [ ] Define a strategy for migration. Auto conversion scripts? wiki <-> md is easy (pandoc, etc). Translations is tricky. There is also the question of images

## Structure proposal

* Introduction 
  * Welcome & about
  * General stuff from user hub, mouse model, etc..
  * Getting started
  * Tutorials
* Workbenches 
  * Each workbench page
* Python scripting 
  * All the poweruser hub pages
* Development and deployment (python scripting is also development, so... should be some other name) 
  * All the pages from developers hub
* Command reference 
  * All the individual command pages classified by prefix (Std, Draft, FEM, etc...)