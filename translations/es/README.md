# Documentación FreeCAD

Ese es un experimento para reconstruir la documentación FreeCAD en forma más sostenible, basado en Markdown. Por el momento, está hecho únicamente para servir como prueba de concepto, para explorar lo que se puede hacer con los archivos de Markdown y un sistema basado en git, probar diferentes funcionalidades y sistemas para llegar al mismo nivel de eficiencia y apertura que tenemos en la wiki de FreeCAD y, en última instancia, si todo va bien, convencer a la comunidad para que haga el cambio.

## Metas

* Tener una presentación mas profesional y estructurada, fácil de navegar y que utiliza documentación que tenemos actualmente en la wiki
* Ser más fácil de administrar, "respaldable" y portátil que la wiki actual
* Sea más fácil de cargar en un paquete de documentación fuera de línea para agruparlo con FreeCAD
* Ofrecer el mismo nivel de facilidad a las personas que quieran colaborar
* Ofrecer un buen sistema de traducción que sea fácil de usar para las personas que quieran traducir
* Ofrecer "versiones" de documentación que correspondan a las versiones de FreeCAD
* Ofrecer documentación en formatos adecuados para lectores fuera de línea: ePub, pdf, etc.
* También se pueden integrar aquí archivos de ejemplo

## Ventajas

* Markdown es [ fácil, muy similar ](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) a la sintaxis wiki, además de que está más extendido y es más fácil para convertir a otros formatos (más convertidores disponibles) e integrar en otras plataformas que pueden hacer algunas otras tareas automáticamente. Hay muchos scripts como pandoc que se pueden convertir a/desde la sintaxis wiki automáticamente, pero la conversión a mano también es bastante fácil
* Muchas cosas sofisticadas que tenemos que hacer con los complementos en la wiki están incorporadas en Markdown, como imágenes SVG o resaltado de sintaxis de código
* La interfaz de github es tan cómoda o incluso más cómoda que trabajar con mediawiki. Puede trabajar completamente desde dentro de la interfaz de github (incluida la carga de imágenes, etc.) y no necesita preocuparse por las cosas de git
* También puede trabajar sin conexión y extraer/empujar como un git normal, luego tiene editores WYSIWYG adicionales y hermosos como [ typora ](https://typora.io) (no más ventanas de edición/vista previa)
* El flujo de trabajo de git permite un sistema de gestión más fino: los colaboradores frecuentes y de confianza pueden tener acceso de escritura, mientras que los colaboradores ocasionales pueden hacer PR´s sin tener que solicitar permiso
* Git resuelve problemas de copia de seguridad: todos los que clonan el repositorio tienen una copia completa, por lo que el código se duplica en muchas ubicaciones
* Dado que todo está basado en archivos, es muy fácil mover y reorganizar las cosas
* Sincronización automática con [ gitbook ](https://legacy.gitbook.com/book/yorikvanhavre/freecad-documentation), por lo que toda la documentación está siempre disponible en formato pdf, epub y mobi, automáticamente. Todo lo que requiere es mantener actualizado el archivo [ SUMMARY.md ](SUMMARY.md). Otros sistemas como [ ReadTheDocs ](https://readthedocs.org/projects/freecad-documentation/) o [ MkDocs ](http://www.mkdocs.org/) son fáciles de configurar para compilar automáticamente también.

Así es como aparece en GitBook, se puede leer en línea o descargar como libro electrónico:

![](images/gitbook.png)

* Sincronización automática con [ crowdin ](https://crowdin.com/project/freecad-documentation). Cualquier cambio realizado en github se refleja automáticamente en crowdin (no es necesaria una sincronización manual). Crowdin, a su vez, empuja todos sus cambios en una rama separada en este repositorio, que se puede fusionar en cualquier momento, cuando lo consideremos oportuno, con el clic de un botón. 
* Cada traducción es una copia completa de la estructura de la fuente en inglés, dentro del directorio de "translations". Cada traducción se puede construir y navegar exactamente de la misma manera que la en inglés, y no abarrotan el árbol de fuentes en inglés
* La interfaz de Crowdin para editar archivos de Markdown es un poco diferente a la que usamos para traducir FreeCAD, y es bastante similar al complemento de traducción wiki

Así es como aparece la interfaz de crowdin cuando se trabaja con archivos md:

![](images/crowdin.png)

* Crowdin crea una copia completa de la documentación para cada idioma. Esto simplifica mucho la creación de versiones traducidas completas
* Con Git podemos trabajar con directorios, subdirectorios, etc., lo que facilita la organización de archivos, en comparación con la estructura "plana" de mediawiki
* Con las etiquetas git podemos marcar una determinada versión del documento, por ejemplo, al lanzarlo. También podemos crear ramas para páginas aún no publicadas

## Desventajas

* Es necesario mover todo el wiki, página por página. Algo de esto se puede hacer automáticamente, pero en cualquier caso, la mayoría de los enlaces deberán ser revisados/cambiados, por lo que será necesario revisar manualmente cada página de todos modos
* Las traducciones no se pueden exportar automáticamente. Será un trabajo largo de copiar y pegar.
* La interfaz de Crowdin, aunque elegante para trabajar con archivos de Markdown, tiene algo molesto con los enlaces (aparecen como elementos <a> html). Sin embargo, podríamos lograr hablar de eso con la gente de crowdin y hacer algo...</li> </ul> 
  
  <h2>
    Documentación fuera de línea en FreeCAD
  </h2>
  
  <ul>
    <li>
      En un primer paso, adaptar la generación de documentos fuera de línea es fácil, porque de todos modos se genera a partir de páginas html, y tendremos las mismas páginas en github.
    </li>
    <li>
      En un segundo paso, podemos explorar algo más útil que el documento actual sin conexión basado en asistente de qt, tal vez algo que muestre las páginas html directamente, ya sea en línea o fuera de línea...
    </li>
  </ul>
  
  <h2>
    Conversión Mediawiki -> Markdown
  </h2>
  
  <p>
    Utilizando la conversión automática de la wiki <-> md es fácil, hay muchos scripts disponibles (<a href="http://pandoc.org/">pandoc</a> u otros <a href="https://github.com/Gozala/markdown-wiki">scripts</a>). Las traducciones son complicadas. También está la cuestión de las imágenes. También hay <a href="https://github.com/philipashlock/mediawiki-to-markdown"> herramientas de migración</a>completas, que aún debo probar
  </p>
  
  <p>
    <strong>Manera rápida de convertir:</strong>
  </p>
  
  <p>
    1) Vaya a http://www.freecadweb.org/wiki/Special:Export/Arch_Wall 2) Guarde el xml en su computadora 2) Guarde todas las imágenes de la wiki y cárguelas en github (dentro de una subcarpeta de imágenes) 3) <code>pandoc --from mediawiki --to markdown Arch_Wall.xml</code> opcionalmente, agregue<code>--wrap = none</code> 4) Cree un nuevo archivo, pegue, corrija enlaces
  </p>
  
  <h2>
    Propuesta de estructura
  </h2>
  
  <p>
    Cada una de las categorías siguientes es una carpeta. Cada uno de ellos contiene una subcarpeta de "imágenes" donde van todas las imágenes de las páginas que están dentro de esa categoría.
  </p>
  
  <ul>
    <li>
      Introducción <ul>
        <li>
          Bienvenido & acerca de
        </li>
        <li>
          Cosas generales del centro de usuario, modelo de mouse, etc..
        </li>
        <li>
          Empezando
        </li>
        <li>
          Tutoriales
        </li>
      </ul>
    </li>
    <li>
      Bancos de trabajo <ul>
        <li>
          Cada página de banco de trabajo
        </li>
        <li>
          Quizás también enlaces a bancos de trabajo externos?
        </li>
      </ul>
    </li>
    <li>
      Python scripting <ul>
        <li>
          Todas las páginas del centro de usuarios avanzados
        </li>
      </ul>
    </li>
    <li>
      Desarrollo e implementación (la secuencia de comandos de Python también es desarrollo, así que... debería ser otro nombre) <ul>
        <li>
          Todas las páginas del centro de desarrolladores
        </li>
      </ul>
    </li>
    <li>
      Referencia de comandos <ul>
        <li>
          Todas las páginas de comandos individuales clasificadas por prefijo (Std, Draft, FEM, etc...)
        </li>
      </ul>
    </li>
    <li>
      Traducciones <ul>
        <li>
          Copias de todo el árbol de documentos en todos los idiomas
        </li>
      </ul>
    </li>
  </ul>