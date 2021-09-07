# FreeCAD документація

Це експеримент з реконструкції документації FreeCAD більш стійкою, на основі оцінки. Саме на даний момент він виключно зроблено для того, щоб слугувати доказом концепції, щоб вивчити, що можливо зробити з файлами змаркування та системою на основі git, протестувати різні функції та системи, щоб досягти такого рівня ефективністі та відкритості, яку ми маємо на вікі в FreeCAD, і, в кінцевому підсумку, якщо все буде добре, переконати громаду зробити перемикач.

## Цілі

* Мати більш структуровану, професійну і зручну навігацію для використання документації, ніж є на вікі
* Бути більш керованими, "резервними" і портативними, ніж поточна вікі
* Бути легшим для пакування в офлайн документацію, що буде у комплекті з FreeCad
* Запропонувати такий же рівень легкості для людей, які хочуть співпрацювати
* Запропонувати гарну систему перекладу, яка була б простою у використанні людьми, які бажають перекладати
* Запропонувати "версії" документацій, які відносяться до релізів FreeCAD
* Запропонувати документацію у форматах які підходять для офлайн читача - ePub, pdf, тощо.
* Також сюди можуть бути інтегровані файли прикладів

## Переваги

* Markdown is [easy, very similar](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to the wiki syntax, plus it is more widespread and easier to convert to other formats (more convertors available) and integrate into other platforms that can do some other tasks automatically. Є багато скриптів, таких як pandoc, які можуть автоматично двонаправлено конвертувати вікі синтаксис, але ручне перетворення є також досить легким
* Багато фантастичних речей, які ми робимо за допомоою плагінів у вікі є вбудовані в markdown, такі як SVG-зображення або підсвічування синтаксису коду
* Інтерфейс Github є таким же або навіть більш зручним для роботи, ніж mediawiki. Ви можете працювати повністю зсередини github інтерфейсу (включаючи завантаження зображення і т. д.) і не потрібно піклуватися про git stuff
* Ви можете також працювати офлайні та pull/push як нормальний git, то у вас є додаткові, чудові WYSIWYG редактори на кшталт [typora](https://typora.io) (більше не потрібно вікон редагування/попереднього перегляду)
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
* The Crowdin interface, although elegant to work wik markdown files, has an annoying thing with links (they appear as <a> html elements). However, we might succeed in talking about that with crowdin people and do something...</li> </ul> </li> </ul> 
    
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
      <strong>Швидкий спосіб конвертації:</strong>
    </p>
    
    <p>
      1) Go to http://www.freecadweb.org/wiki/Special:Export/Arch_Wall 2) Save the xml on your computer 2) Save all images from the wiki and upload them to github (inside an images subfolder) 3) <code>pandoc --from mediawiki --to markdown Arch_Wall.xml</code> optionally, add <code>--wrap=none</code> 4) Create a new file, paste, fix links
    </p>
    
    <h2>
      Структурна пропозіція
    </h2>
    
    <p>
      Each of the categories below is a folder. Each of them contains an "images" subfolder where all the images of the pages that are inside that categoriy go.
    </p>
    
    <ul>
      <li>
        Вступ <ul>
          <li>
            Welcome & about
          </li>
          <li>
            General stuff from user hub, mouse model, etc..
          </li>
          <li>
            З чого почати
          </li>
          <li>
            Tutorials
          </li>
        </ul>
      </li>
      <li>
        Робочі простори <ul>
          <li>
            Сторінка кожного робочого простору
          </li>
          <li>
            Можливо, також посилання на сторонні робочі простори?
          </li>
        </ul>
      </li>
      <li>
        Cтворення скриптів на Python <ul>
          <li>
            Усі сторінки хабу poweruser
          </li>
        </ul>
      </li>
      <li>
        Розробка та розгортання (написання скриптів на Python також розробка, то ж... має бути якась інша назва) <ul>
          <li>
            Усі сторінки з хабу розробників
          </li>
        </ul>
      </li>
      <li>
        Командний довідник <ul>
          <li>
            Усі індивідуальні сторінки команд, розсортовані за префіксами (Std, Draft, FEM, та ін.)
          </li>
        </ul>
      </li>
      <li>
        Переклади <ul>
          <li>
            Копії всього дерева документів кожною мовою
          </li>
        </ul>
      </li>
    </ul>