# Документация FreeCAD

Это эксперимент по реконструкции документации FreeCAD более устойчивым и основанным на языке разметки способом. В настоящее время она создана исключительно для того, чтобы служить в качестве доказательства концепции, исследовать, что можно сделать с файлами разметки и системы на базе git, тестировать различные функции и системы, чтобы достичь того же уровня эффективности и открытости, что мы имеем на вики FreeCAD, в конце концов, если все пойдет хорошо, убедить сообщество перейти на этот формат.

## Цели

* Иметь более структурированную, профессиональную и удобную для навигации и использования документацию, чем мы имеем в настоящее время на вики
* Быть более легко управляемым, устойчивым и портативным, чем текущий вики
* Упростить упаковку в автономный пакет документации, который будет поставляться с FreeCAD
* Предложить такой же уровень простоты людям, желающим сотрудничать
* Предложить хорошую систему перевода, которая проста в использовании для людей, желающих переводить
* Предлагать «версии» документации, соответствующие выпускам FreeCAD
* Предлагать документацию в форматах, подходящих для электронных книг - ePub, pdf и т. д.
* Здесь также можно интегрировать файлы примеров

## Преимущества

* Разметка [ проста, очень похожа ](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) на синтаксис вики, плюс она более широко распространена и легче конвертируется в другие форматы (доступно больше конвертеров) и интегрируется в другие платформы, которые могут выполнять некоторые другие задачи автоматически. Существует много сценариев, таких как pandoc, которые могут преобразовать в/из Wiki синтаксиса автоматически, но преобразование вручную также довольно легко сделать
* Многие интересные вещи, которые мы должны делать с плагинами в вики являются встроенными в разметку, например изображения SVG или подсветка синтаксиса кода
* Интерфейс github такой же удобный или даже более удобный, чем Mediawiki. Вы можете полностью работать внутри интерфейса github (включая загрузку изображений и т. д.) и не нужно заботиться о материалах git
* You can also work offline and pull/push like normal git, then you have additional, gorgeous WYSIWYG editors like [typora](https://typora.io) (no more edit/preview windows)
* The git workflow allows a finer management system: Frequent, trusted contributors can be granted write access, while occasional contributors can make PRs without having to request permission
* Git solves backup issues: Everybody who clones the repo has a full copy, so the code is duplicated in many locations
* Since it is all file-based, it is very easy to move and reorganize things
* Automatically syncing with [gitbook](https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation), so the whole documentation is always available in pdf, epub and mobi formats, automatically. All it requires is maintaining the <SUMMARY.md> file updated. Other systems such as [ReadTheDocs](https://readthedocs.org/projects/freecad-documentation/) or [MkDocs](http://www.mkdocs.org/) are easy to configure to build automatically too.

This is how it appears on GitBook, it can be read online or downloaded as ebook:

![](images/gitbook.png)

* Automatically syncing with [crowdin](https://crowdin.com/project/freecad-documentation). Any change done on github reflects automatically on crowdin (no manual syncing necessary). Crowdin, in turn, pushes all its changes in a separate branch on this repo, that can be merged any time, when we see fit, with the click of a button. 
* Each translation is a complete copy of the english source structure, inside the "translations" directory. Each translation can be built and browsed the exact same way as the english one, and they don't clutter the english source tree
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
    Offline doc in FreeCAD
  </h2>
  
  <ul>
    <li>
      In a first step, adapting the offline doc generation is easy, because it is anyway generated from html pages, and we will have the same pages on github.
    </li>
    <li>
      In a second step, we can explore something handier thatn the current qt assistant-based offline doc, maybe something that displays the html pages directly, being o line or offline...
    </li>
  </ul>
  
  <h2>
    Mediawiki -> Markdown conversion
  </h2>
  
  <p>
    Using auto conversion scripts wiki <-> md is easy, many scripts available (<a href="http://pandoc.org/">pandoc</a>, or other <a href="https://github.com/Gozala/markdown-wiki">scripts</a>). Translations is tricky. There is also the question of images. There are complete <a href="https://github.com/philipashlock/mediawiki-to-markdown">migration tools</a> too, that I must still test
  </p>
  
  <p>
    <strong>Quick way to convert:</strong>
  </p>
  
  <p>
    1) Go to http://www.freecadweb.org/wiki/Special:Export/Arch_Wall 2) Save the xml on your computer 2) Save all images from the wiki and upload them to github (inside an images subfolder) 3) <code>pandoc --from mediawiki --to markdown Arch_Wall.xml</code> optionally, add <code>--wrap=none</code> 4) Create a new file, paste, fix links
  </p>
  
  <h2>
    Structure proposal
  </h2>
  
  <p>
    Each of the categories below is a folder. Each of them contains an "images" subfolder where all the images of the pages that are inside that categoriy go.
  </p>
  
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
    <li>
      Translations <ul>
        <li>
          Copies of the whole doc tree in every language
        </li>
      </ul>
    </li>
  </ul>