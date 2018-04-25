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

* Markdown is [easy, very similar](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to the wiki syntax, plus it is more widespread and easier to convert to other formats (more convertors available). There are many scripts like pandoc that can convert to/from wiki syntax automatically, but converting by hand is also pretty easy
* Many fancy things we have to do with plugins on the wiki are builtin in markdown, such as SVG images or code syntax highlighting
* The github interface is as comfortable or even more comfortable than mediawiki to work with. You can work fully from inside the github interface (including image upload, etc) and don't need to careabout git stuff
* You can also work offline and pull/push like normal git, then you have additional, gorgeous WYSIWYG editors like [typora](https://typora.io) (no more edit/preview windows)
* The git workflow allows a finer management system: Frequent, trusted contributors can be granted write access, while occasional contributors can make PRs without having to request permission
* Git solves backup issues: Everybody who clones the repo has a full copy, so the code is duplicated in many locations
* Automatically syncing with [gitbook](https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation), so the whole documentation is always available in pdf, epub and mobi formats, automatically. All it requires is maintaining the <SUMMARY.md> file updated

This is how it appears on GitBook, it can be read online or downloaded as ebook:

![](images/gitbook.png)

* Automatically syncing with [crowdin](https://crowdin.com/project/freecad-documentation). Any change done on github reflects automatically on crowdin (no manual syncing necessary). Crowdin, in turn, pushes all its changes in a separate branch on this repo, that can be merged any time, when we see fit, with the click of a button
* Crowdin's interface for editing markdown files is a bit different than the one we use to translate FreeCAD, and is pretty similar to the wiki translation plugin

This is how the crowdin interface appears when working with md files:

![](images/crowdin.png)

* Crowdin creates a full copy of the documentation for every language. This simplifies a lot the creation of full translated versions
* With Git we can work with directories, subdirectories, etc, which makes organization of files easier, compared to the "flat" structure of mediawiki
* With git tags we can mark a certain version of the doc, for example when releasing. We can also create branches for not-released-yet pages

## Disadvantages

* One needs to move all the wiki, page by page. Some of this can be done automatically, but in any case most of the links will need to be checked/changed, so it will need manual review of each page anyway
* Translations cannot be exported automatically. It will be a long copy/paste work.
* The Crowdin interface, although elegant to work wik markdown files, has an annoying thing with links (they appear as <a> html elements). However, we might succeed in talking about that with crowdin people and do something...</li> </ul> 
  
  <h2>
    TODO
  </h2>
  
  <ol>
    <li>
      [ ] Define a better structure than the user hub / power user hub / developers hub of the wiki? Are these hubs entirely necessary? The wiki structure is "flat" (all pages are at the same level, and can be part of categories), the directory structure of git can allow something more structurated
    </li>
    
    <li>
      [ ] Define how to cope with the command reference. This is the main subject of the offline doc, it should be handled with extra importance. Also find a way to identify missing command pages, etc...
    </li>
    
    <li>
      [x] Link with docbook (will create the "book workflow" + pdf, ebook... automatically). Basically need to update <a href="SUMMARY.md">SUMMARY.md</a> DONE - https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation
    </li>
    
    <li>
      [x] Check how translation systems can handle this: crowdin (preferred), transifex? Both support md files, check what would be easier to manage (ideally something automatic?) DONE - https://crowdin.com/project/freecad-documentation
    </li>
    
    <li>
      [ ] Define a strategy for migration. Auto conversion scripts? wiki <-> md is easy (pandoc, etc). Translations is tricky. There is also the question of images
    </li>
  </ol>
  
  <h2>
    Structure proposal
  </h2>
  
  <ul>
    <li>
      Introduction <ul>
        <li>
          Welcome & about
        </li>
        <li>
          General stuff from user hub, mouse model, etc..
        </li>
        <li>
          Getting started
        </li>
        <li>
          Tutorials
        </li>
      </ul>
    </li>
    <li>
      Workbenches <ul>
        <li>
          Each workbench page
        </li>
        <li>
          Maybe links to external workbenches too?
        </li>
      </ul>
    </li>
    <li>
      Python scripting <ul>
        <li>
          All the poweruser hub pages
        </li>
      </ul>
    </li>
    <li>
      Development and deployment (python scripting is also development, so... should be some other name) <ul>
        <li>
          All the pages from developers hub
        </li>
      </ul>
    </li>
    <li>
      Command reference <ul>
        <li>
          All the individual command pages classified by prefix (Std, Draft, FEM, etc...)
        </li>
      </ul>
    </li>
  </ul>