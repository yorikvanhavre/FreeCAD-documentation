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

## Advantages

* Markdown is [easy, very similar](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to the wiki syntax, plus it is more widespread and easier to convert to other formats (more convertors available) and integrate into other platforms that can do some other tasks automatically. There are many scripts like pandoc that can convert to/from wiki syntax automatically, but converting by hand is also pretty easy
* Many fancy things we have to do with plugins on the wiki are builtin in markdown, such as SVG images or code syntax highlighting
* The github interface is as comfortable or even more comfortable than mediawiki to work with. You can work fully from inside the github interface (including image upload, etc) and don't need to careabout git stuff
* You can also work offline and pull/push like normal git, then you have additional, gorgeous WYSIWYG editors like [typora](https://typora.io) (no more edit/preview windows)
* The git workflow allows a finer management system: Frequent, trusted contributors can be granted write access, while occasional contributors can make PRs without having to request permission
* Git solves backup issues: Everybody who clones the repo has a full copy, so the code is duplicated in many locations
* Automatically syncing with [gitbook](https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation), so the whole documentation is always available in pdf, epub and mobi formats, automatically. All it requires is maintaining the [SUMMARY.md](SUMMARY.md) file updated. Other systems such as [ReadTheDocs](https://readthedocs.org/projects/freecad-documentation/) or [MkDocs](http://www.mkdocs.org/) are easy to configure to build automatically too.

This is how it appears on GitBook, it can be read online or downloaded as ebook:

![](images/gitbook.png)

* Automatically syncing with [crowdin](https://crowdin.com/project/freecad-documentation). Any change done on github reflects automatically on crowdin (no manual syncing necessary). Crowdin, in turn, pushes all its changes in a separate branch on this repo, that can be merged any time, when we see fit, with the click of a button. 
* Each translation is a complete copy of the english source structure, inside the "translations" directory. Each translation can be built and browsed the exact same way as the english one, and they don't clutter the english source tree
* Crowdin's interface for editing markdown files is a bit different than the one we use to translate FreeCAD, and is pretty similar to the wiki translation plugin

This is how the crowdin interface appears when working with md files:

![](images/crowdin.png)

* Crowdin creates a full copy of the documentation for every language. This simplifies a lot the creation of full translated versions
* With Git we can work  with directories, subdirectories, etc, which makes organization of files easier, compared to the "flat" structure of mediawiki
* With git tags we can mark a certain version of the doc, for example when releasing. We can also create branches for not-released-yet pages

## Disadvantages

* One needs to move all the wiki, page by page. Some of this can be done automatically, but in any case most of the links will need to be checked/changed, so it will need manual review of each page anyway
* Translations cannot be exported automatically. It will be a long copy/paste work.
* The Crowdin interface, although elegant to work wik markdown files, has an annoying thing with links (they appear as <a> html elements). However, we might succeed in talking about that with crowdin people and do something...

## Offline doc in FreeCAD

* In a first step, adapting the offline doc generation is easy, because it is anyway generated from html pages, and we will have the same pages on github. 
* In a second step, we can explore something handier thatn the current qt assistant-based offline doc, maybe something that displays the html pages directly, being o line or offline...

## Mediawiki -> Markdown conversion

Using auto conversion scripts wiki <-> md is easy, many scripts available ([pandoc](http://pandoc.org/), or other [scripts](https://github.com/Gozala/markdown-wiki)). Translations is tricky. There is also the question of images. There are complete [migration tools](https://github.com/philipashlock/mediawiki-to-markdown) too, that I must still test

**Quick way to convert:**

1) Go to http://www.freecadweb.org/wiki/Special:Export/Arch_Wall 
2) Save the xml on your computer
2) Save all images from the wiki and upload them to github (inside an images subfolder) 
3) `pandoc --from mediawiki --to markdown Arch_Wall.xml` optionally, add `--wrap=none`
4) Create a new file, paste, fix links

## Structure proposal

Each of the categories below is a folder. Each of them contains an "images" subfolder where all the images of the pages that are inside that categoriy go.

* Introduction
  * Welcome & about
  * General stuff from user hub, mouse model, etc..
  * Getting started
  * Tutorials
* Workbenches
  * Each workbench page
  * Maybe links to external workbenches too?
* Python scripting
  * All the poweruser hub pages
* Development and deployment (python scripting is also development, so... should be some other name)
  * All the pages from developers hub
* Command reference
  * All the individual command pages classified by prefix (Std, Draft, FEM, etc...)
* Translations
  * Copies of the whole doc tree in every language
